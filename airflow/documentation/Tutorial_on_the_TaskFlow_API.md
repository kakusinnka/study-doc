# Working with TaskFlow
本教程以常规 Airflow 教程为基础，特别关注使用作为 Airflow 2.0 的一部分引入的 TaskFlow API 范例编写数据管道，并将其与使用传统范例编写的 DAG 进行对比。

```

import json

import pendulum

from airflow.decorators import dag, task

# 我们正在创建一个 DAG，它是我们的任务的集合，任务之间存在依赖关系。
# 在这个例子中，请注意我们使用@dag 装饰器创建这个 DAG，如下所示，Python 函数名称作为 DAG 标识符。
@dag(
    schedule=None,
    start_date=pendulum.datetime(2021, 1, 1, tz="UTC"),
    catchup=False,
    tags=['example'],
)
def tutorial_taskflow_api():
    """
    ### TaskFlow API Tutorial Documentation
    This is a simple data pipeline example which demonstrates the use of
    the TaskFlow API using three simple tasks for Extract, Transform, and Load.
    Documentation that goes along with the Airflow TaskFlow API tutorial is
    located
    [here](https://airflow.apache.org/docs/apache-airflow/stable/tutorial_taskflow_api.html)
    """
    # 任务是基于 Python 函数使用 @task 装饰器创建的。函数名称充当任务的唯一标识符。
    @task()
    def extract():
        """
        #### Extract task
        A simple Extract task to get data ready for the rest of the data
        pipeline. In this case, getting data is simulated by reading from a
        hardcoded JSON string.
        """
        data_string = '{"1001": 301.27, "1002": 433.21, "1003": 502.22}'

        order_data_dict = json.loads(data_string)
        return order_data_dict
    @task(multiple_outputs=True)
    def transform(order_data_dict: dict):
        """
        #### Transform task
        A simple Transform task which takes in the collection of order data and
        computes the total order value.
        """
        total_order_value = 0

        for value in order_data_dict.values():
            total_order_value += value

        return {"total_order_value": total_order_value}
    @task()
    def load(total_order_value: float):
        """
        #### Load task
        A simple Load task which takes in the result of the Transform task and
        instead of saving it to end user review, just prints it out.
        """

        print(f"Total order value is: {total_order_value:.2f}")
    # 我们调用了 Extract 任务，从那里获取订单数据并将其发送到 Transform 任务进行汇总，然后使用汇总数据调用 Load 任务。
    # 任务之间的依赖关系以及这些任务之间的数据传递（可能在网络上不同节点上的不同工作人员上运行）都由 Airflow 处理。
    order_data = extract()
    order_summary = transform(order_data)
    load(order_summary["total_order_value"])

# 现在要真正让它作为 DAG 运行，我们调用前面使用 @dag 装饰器设置的 Python 函数 tutorial_taskflow_api。
tutorial_taskflow_api()
```

## Using the TaskFlow API with Docker or Virtual Environments
如果您有需要复杂或冲突要求的任务，那么您将能够将 TaskFlow API 与 Docker 容器（自 2.2.0 版起）或 Python 虚拟环境（2.0.2 版起）一起使用。
暂且理解为不同的worker使用自己独立的环境 (docker) (Virtual Env)。

## Multiple outputs inference (推断)
任务还可以通过使用 dict Python 类型来推断多个输出。
```
@task
def identity_dict(x: int, y: int) -> Dict[str, int]:
    return {"x": x, "y": y}
```

## 在装饰任务(@Task)和传统任务之间添加依赖关系
```
# 它从已知文件位置读取数据
@task()
def extract_from_file():
    """
    #### 从文件中提取数据的任务
    一个简单的提取任务，通过将文件中的数据读取到 pandas 数据帧中，为数据管道的其余部分准备好数据
    """
    order_data_file = "/tmp/order_data.csv"
    order_data_df = pd.read_csv(order_data_file)

# FileSensor 任务来检查这个文件。这是一个等待文件的 感应器 任务。
file_task = FileSensor(task_id="check_file", filepath="/tmp/order_data.csv")
# 指定此 Sensor 任务和 TaskFlow 函数之间的依赖关系。
order_data = extract_from_file()

file_task >> order_data
```

## 在装饰任务(@Task)和传统任务之间使用 XCom
使用 .output
```
my_op = MyOperator(...)
my_op_output = my_op.output["some_other_xcom_key"]
# OR
my_op_output = my_op.output.get("some_other_xcom_key")
```
```
get_api_results_task = SimpleHttpOperator(
    task_id="get_api_results",
    endpoint="/api/query",
    do_xcom_push=True,
    http_conn_id="http",
)


@task(max_retries=2)
def parse_results(api_results):
    return json.loads(api_results)


parsed_results = parse_results(api_results=get_api_results_task.output)
```
```
BASE_PATH = "salesforce/customers"
FILE_NAME = "customer_daily_extract_{{ ds_nodash }}.csv"


upload_salesforce_data_to_s3_landing = SalesforceToS3Operator(
    task_id="upload_salesforce_data_to_s3",
    salesforce_query="SELECT Id, Name, Company, Phone, Email, LastModifiedDate, IsActive FROM Customers",
    s3_bucket_name="landing-bucket",
    s3_key=f"{BASE_PATH}/{FILE_NAME}",
    salesforce_conn_id="salesforce",
    aws_conn_id="s3",
    replace=True,
)


store_to_s3_data_lake = S3CopyObjectOperator(
    task_id="store_to_s3_data_lake",
    aws_conn_id="s3",
    source_bucket_key=upload_salesforce_data_to_s3_landing.output,
    dest_bucket_name="data_lake",
    dest_bucket_key=f"""{BASE_PATH}/{"{{ execution_date.strftime('%Y/%m/%d') }}"}/{FILE_NAME}""",
)
```

## 在装饰任务(@Task)中访问上下文变量
```
@task
def my_python_callable(ti=None, next_ds=None):
    pass
```
```
@task
def my_python_callable(**kwargs):
    ti = kwargs["ti"]
    next_ds = kwargs["next_ds"]
```
```
from airflow.operators.python import get_current_context

# 当前上下文只能在任务执行期间访问。
def some_function_in_your_library():
    context = get_current_context()
    ti = context["ti"]
```