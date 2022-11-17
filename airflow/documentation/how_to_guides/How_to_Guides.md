# How-to Guides
## 向 DAG 添加标签并将其用于 UI 中的过滤
```
dag = DAG(dag_id="example_dag_tag", schedule="0 0 * * *", tags=["example"])
```

## 将所有者链接添加到 DAG
```
dag = DAG(
    dag_id="example_dag_owners",
    schedule="0 0 * * *",
    start_date=datetime(2022, 8, 5),
    owner_links={"airflow": "https://airflow.apache.org/"},
)

with dag:
    bash_task = BashOperator(task_id='task_using_linked_owner', bash_command='echo 1', owner='airflow')
```

## 设置配置选项
* 第一次运行 Airflow 时，它会在 $AIRFLOW_HOME 目录（默认为 ~/airflow）中创建一个名为 airflow.cfg 的文件。此文件包含 Airflow 的配置，您可以对其进行编辑以更改任何设置。
```
[database]
sql_alchemy_conn = my_conn_string
```
* 您还可以使用以下格式设置环境变量选项：AIRFLOW__{SECTION}__{KEY}（注意双下划线）。
```
export AIRFLOW__DATABASE__SQL_ALCHEMY_CONN=my_conn_string
```

* 您还可以在运行时通过将 _cmd 附加到键来派生连接字符串
```
[database]
sql_alchemy_conn_cmd = bash_command_to_run
```

* 您还可以通过将 _secret 附加到密钥来在运行时派生连接字符串
```
[database]
sql_alchemy_conn_secret = sql_alchemy_conn
# 您还可以添加嵌套路径
# example:
# sql_alchemy_conn_secret = database/sql_alchemy_conn
```

* _cmd 配置选项也可以使用相应的环境变量来设置，就像通常的配置选项一样。
```
export AIRFLOW__DATABASE__SQL_ALCHEMY_CONN_CMD=bash_command_to_run
```

* _secret 配置选项也可以使用相应的环境变量进行设置。
```
export AIRFLOW__DATABASE__SQL_ALCHEMY_CONN_SECRET=sql_alchemy_conn
```

* 您可以使用以下命令检查当前配置。
```
airflow config get-value
```
* 如果您只想查看一个选项的值，可以使用以下命令
```
$ airflow config get-value core executor
SequentialExecutor
```

## 设置数据库后端
Set_up_Database_Backend.md

## Using Operators
Using_Operators.md

## Customizing DAG Scheduling with Timetables (使用时间表自定义 DAG 调度)
Customizing_DAG_Scheduling_with_Timetables.md

## Customizing the UI
* 自定义状态颜色
* 自定义 DAG UI 标题和 Airflow 页面标题
* 在仪表板上添加自定义警报消息

## 创建自定义运算符
些许有些难。。。暂且先跳过。
* 挂钩
* 用户界面
* 模板化
* 定义一个运算符额外链接
* 传感器

## 创建自定义 @task 装饰器
些许有些难。。。暂且先跳过。
*（可选）添加IDE自动补全支持

## 管理连接
ManagingConnections.md