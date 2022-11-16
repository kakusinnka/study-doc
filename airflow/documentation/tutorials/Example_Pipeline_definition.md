# 示例管道定义
* 这是一个 DAG 定义文件。人们有时将DAG定义文件视为可以进行一些实际数据处理的地方 - 完全不是这样！ 脚本的目的是定义DAG对象。
* Airflow 管道只是一个 Python 脚本，它恰好定义了一个 Airflow DAG 对象。
```
from datetime import datetime, timedelta
from textwrap import dedent

# DAG对象； 我们需要它来实例化DAG
from airflow import DAG

# Operators(操作员); we need this to operate(操作)!
from airflow.operators.bash import BashOperator

# 我们需要一个 DAG 对象来嵌套我们的任务。
with DAG(
    # 在这里，我们传递了一个定义 dag_id 的字符串，它用作 DAG 的唯一标识符。
    'tutorial',
    # 默认参数字典
    # 我们即将创建一个 DAG 和一些任务，我们可以选择显式地将一组参数传递给每个任务的构造函数。
    # 这些参数将传递给每个Operators(操作员)。
    # 您可以在Operators(操作员)初始化期间基于每个任务覆盖它们。
    default_args={
        # 通过将depends_on_past 设置为true，此任务将不会运行，除非前一个任务成功。
        'depends_on_past': False,
        'email': ['airflow@example.com'],
        'email_on_failure': False,
        'email_on_retry': False,
        'retries': 1,
        'retry_delay': timedelta(minutes=5),
        # 'queue': 'bash_queue',
        # 'pool': 'backfill',
        # 'priority_weight': 10,
        # 'end_date': datetime(2016, 1, 1),
        # 'wait_for_downstream': False,
        # 'sla': timedelta(hours=2),
        # 'execution_timeout': timedelta(seconds=300),
        # 'on_failure_callback': some_function,
        # 'on_success_callback': some_other_function,
        # 'on_retry_callback': another_function,
        # 'sla_miss_callback': yet_another_function,
        # 'trigger_rule': 'all_success'
    },
    # 描述
    description='A simple tutorial DAG',
    # 时间表
    schedule=timedelta(days=1),
    # 开始时间
    start_date=datetime(2021, 1, 1),
    catchup=False,
    # 标签
    tags=['example'],
) as dag:

    # operator定义 Airflow 完成的工作单元。 使用operator是在 Airflow 中定义工作的经典方法。
    # 所有operator都继承自 BaseOperator，其中包括在 Airflow 中运行工作所需的所有参数。
    # Airflow 根据您传递给operator的参数完成工作。
    # t1, t2 and t3 是 通过实例化operator来创建的task。
    # 要在 DAG 中使用operator，您必须将其实例化为任务。 任务决定了如何在 DAG 的上下文中执行operator的工作。
    # 实例化操作员对象时会生成任务。
    # 在以下示例中，我们将 BashOperator 实例化为两个单独的任务，以便运行两个单独的 bash 脚本。 每个实例化的第一个参数 task_id 充当任务的唯一标识符。
    t1 = BashOperator(
        task_id='print_date',
        bash_command='date',
    )

    t2 = BashOperator(
        task_id='sleep',
        depends_on_past=False,
        bash_command='sleep 5',
        retries=3,
    )
    t1.doc_md = dedent(
        """\
    #### Task Documentation
    You can document your task using the attributes `doc_md` (markdown),
    `doc` (plain text), `doc_rst`, `doc_json`, `doc_yaml` which gets
    rendered in the UI's Task Instance Details page.
    ![img](http://montcs.bloomu.edu/~bobmon/Semesters/2012-01/491/import%20soul.png)
    **Image Credit:** Randall Munroe, [XKCD](https://xkcd.com/license.html)
    """
    )

    dag.doc_md = __doc__  # 前提是您在 DAG 的开头有一个文档字符串;
    dag.doc_md = """
    This is a documentation placed anywhere
    """  # 否则，像这样输入
    # Airflow 利用 Jinja 模板的强大功能，并为管道作者提供了一组内置参数和宏。
    # Airflow 还为管道作者提供了挂钩来定义自己的参数、宏和模板。
    templated_command = dedent(
        """
        # 包含 {% %} 块中的代码逻辑
    {% for i in range(5) %}
    # 引用参数像这样： {{ ds }}
        echo "{{ ds }}"
        # 调用函数像这样 {{ macros.ds_add(ds, 7)}}
        echo "{{ macros.ds_add(ds, 7)}}"
    {% endfor %}
    """
    )

    t3 = BashOperator(
        task_id='templated',
        depends_on_past=False,
        bash_command=templated_command,
    )

    t1 >> [t2, t3]
```

## 测试
* Running the Script
  - 首先，让我们确保管道解析成功。也就是运行 python 文件
* 命令行元数据验证
```
# 初始化数据库表
airflow db init

# 打印活动 DAG 列表
airflow dags list

# 打印 "tutorial" DAG 中的任务列表
airflow tasks list tutorial

# 在 "tutorial" DAG 中打印任务的层次结构
airflow tasks list tutorial --tree
```
* Test
  - 让我们通过运行特定日期的实际任务实例来进行测试。
  ```
  airflow tasks test dag_id task_id date
  airflow tasks test tutorial print_date 2015-06-01
  
  airflow dags test [dag_id] [logical_date]
  ```
  - 测试不会在数据库中注册任何状态。
* Backfill