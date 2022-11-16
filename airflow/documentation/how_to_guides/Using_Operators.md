# Using Operators 使用操作员
操作员确定 DAG 运行时实际执行的内容。

## BashOperator
* 使用 BashOperator 在 Bash shell 中执行命令。
```
run_this = BashOperator(
    task_id='run_after_loop',
    bash_command='echo 1',
)
```

* 您可以使用 [Jinja templates](https://airflow.apache.org/docs/apache-airflow/stable/concepts/operators.html#concepts-jinja-templating) 来参数化 bash_command 参数。
```
also_run_this = BashOperator(
    task_id='also_run_this',
    bash_command='echo "ti_key={{ task_instance_key_str }}"',
)
```

* 通常，非零退出代码会产生 AirflowException，从而导致任务失败。 如果希望任务以跳过状态结束，您可以使用代码 99 退出。
```
this_will_skip = BashOperator(
    task_id='this_will_skip',
    bash_command='echo "hello world"; exit 99;',
    dag=dag,
)
```

* 出于多种原因，可能需要为 bash 脚本创建单独的文件夹，例如分离脚本的逻辑和管道代码，允许在由不同语言组成的文件中正确突出显示代码，以及构建管道的一般灵活性。可以将您的 template_searchpath 定义为指向 DAG 构造函数调用中的任何文件夹位置。
```
dag = DAG("example_bash_dag", template_searchpath="/opt/scripts")
t2 = BashOperator(
    task_id="bash_example",
    # "test.sh" is a file under "/opt/scripts"
    bash_command="test.sh ",
    dag=dag,
)
```

## BranchDateTimeOperator
根据时间是否落入两个目标参数给定的范围内，使用 BranchDateTimeOperator 分支到两个执行路径之一，该运算符有两种模式。 第一种模式是使用当前时间（执行 DAG 时的机器时钟时间），第二种模式是使用运行它的 DAG 运行的逻辑日期。
```
dummy_task_1 = DummyOperator(task_id='date_in_range', dag=dag)
dummy_task_2 = DummyOperator(task_id='date_outside_range', dag=dag)

cond1 = BranchDateTimeOperator(
    task_id='datetime_branch',
    follow_task_ids_if_true=['date_in_range'],
    follow_task_ids_if_false=['date_outside_range'],
    target_upper=pendulum.datetime(2020, 10, 10, 15, 0, 0),
    target_lower=pendulum.datetime(2020, 10, 10, 14, 0, 0),
    dag=dag,
)

# Run dummy_task_1 if cond1 executes between 2020-10-10 14:00:00 and 2020-10-10 15:00:00
cond1 >> [dummy_task_1, dummy_task_2]
```
* 当 target_upper < target_lower 时，target_upper 加一天
* 当 target 只有一个不为 None 时，就只比较这一个 target。
* 当两个 target 都为 None 时, 将发生异常。

## PythonOperator
使用 @task 装饰器来执行 Python 可调用对象。推荐使用 @task 装饰器而不是经典的 PythonOperator 来执行 Python 可调用对象。

```
@task(task_id="print_the_context")
def print_context(ds=None, **kwargs):
    """Print the Airflow context and ds variable from the context."""
    pprint(kwargs)
    print(ds)
    return 'Whatever you return gets printed in the logs'

run_this = print_context()
```

* 传入参数  
将额外的参数传递给 @task 修饰函数，就像使用普通 Python 函数一样。

## PythonVirtualenvOperator
* 使用 @task.virtualenv 装饰器在新的 Python 虚拟环境中执行 Python 可调用对象。virtualenv 包需要安装在运行 Airflow 的环境中（作为可选依赖 pip install airflow[virtualenv] --constraint ...）。

* 推荐使用 @task.virtualenv 装饰器而不是经典的 PythonVirtualenvOperator，以在新的 Python 虚拟环境中执行 Python 可调用对象。
```
    @task.virtualenv(
        task_id="virtualenv_python", requirements=["colorama==0.4.0"], system_site_packages=False
    )
    def callable_virtualenv():
        """
        将在虚拟环境中执行的示例函数。

        Importing at the module level ensures that it will not attempt to import the
        library before it is installed.
        """
        from time import sleep

        from colorama import Back, Fore, Style

        print(Fore.RED + 'some red text')
        print(Back.GREEN + 'and with a green background')
        print(Style.DIM + 'and in dim text')
        print(Style.RESET_ALL)
        for _ in range(4):
            print(Style.DIM + 'Please wait...', flush=True)
            sleep(1)
        print('Finished')

    virtualenv_task = callable_virtualenv()
```

## BranchDayOfWeekOperator
使用 BranchDayOfWeekOperator 根据工作日值分支您的工作流。
```
dummy_task_1 = DummyOperator(task_id='branch_true', dag=dag)
dummy_task_2 = DummyOperator(task_id='branch_false', dag=dag)

branch = BranchDayOfWeekOperator(
    task_id="make_choice",
    follow_task_ids_if_true="branch_true",
    follow_task_ids_if_false="branch_false",
    week_day="Monday",
)

# Run dummy_task_1 if branch executes on Monday
branch >> [dummy_task_1, dummy_task_2]
```

## Cross-DAG Dependencies (跨 DAG 依赖)
当两个 DAG 存在依赖关系时，值得考虑将它们组合成一个 DAG，这通常更容易理解。Airflow 还为同一 DAG 上的任务提供了更好的依赖关系可视化表示。  
但是，有时将所有相关任务放在同一个 DAG 上是不切实际的。1, 两个 DAG 可能有不同的时间表。 例如。 每周 DAG 的任务可能依赖于每日 DAG 上的其他任务。2, 不同的团队负责不同的 DAG，但这些 DAG 有一些跨 DAG 的依赖关系。3, 一个任务可能依赖于同一个 DAG 上的另一个任务，但执行日期不同（数据间隔的开始）。将 execution_delta 用于在不同时间运行的任务，例如 execution_delta=timedelta(hours=1) 以检查 1 小时前运行的任务。  
ExternalTaskSensor 可用于跨不同 DAG 建立此类依赖关系。 当它与 ExternalTaskMarker 一起使用时，清除依赖任务也可以跨不同的 DAG 发生。
* ExternalTaskSensor
使用 ExternalTaskSensor 使 DAG 上的任务在特定的 execution_date 等待不同 DAG 上的另一个任务。
ExternalTaskSensor 还提供选项以通过 allowed_states 和 failed_states 参数设置远程 DAG 上的任务是成功还是失败。
```
child_task1 = ExternalTaskSensor(
    task_id="child_task1",
    external_dag_id=parent_dag.dag_id,
    external_task_id=parent_task.task_id,
    timeout=600,
    allowed_states=['success'],
    failed_states=['failed', 'skipped'],
    mode="reschedule",
)
```

* ExternalTaskMarker
```
parent_task = ExternalTaskMarker(
    task_id="parent_task",
    external_dag_id="example_external_task_marker_child",
    external_task_id="child_task1",
)
```

## Customizing DAG Scheduling with Timetables (使用时间表自定义 DAG 调度)


### ExternalPythonOperator
ExternalPythonOperator 可以帮助您使用与其他任务（以及主要 Airflow 环境）不同的 Python 库集来运行某些任务。
```
    @task.external_python(task_id="external_python", python=os.fspath(sys.executable))
    def callable_external_python():
        """
        Example function that will be performed in a virtual environment.

        Importing at the module level ensures that it will not attempt to import the
        library before it is installed.
        """
        import sys
        from time import sleep

        print(f"Running task via {sys.executable}")
        print("Sleeping")
        for _ in range(4):
            print('Please wait...', flush=True)
            sleep(1)
        print('Finished')

    external_python_task = callable_external_python()
```

## ShortCircuitOperator
使用 @task.short_circuit 装饰器来控制在满足条件或获得真值时管道是否继续。
```
@task.short_circuit()
def check_condition(condition):
    return condition

ds_true = [EmptyOperator(task_id='true_' + str(i)) for i in [1, 2]]
ds_false = [EmptyOperator(task_id='false_' + str(i)) for i in [1, 2]]

condition_is_true = check_condition.override(task_id="condition_is_true")(condition=True)
condition_is_false = check_condition.override(task_id="condition_is_false")(condition=False)

chain(condition_is_true, *ds_true)
chain(condition_is_false, *ds_false)
```