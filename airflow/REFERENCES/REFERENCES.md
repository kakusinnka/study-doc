# 参考
## 运算符和钩子

## 命令行界面
CLI.md

## 模板
### 变量
Airflow 引擎默认传递一些在所有模板中都可以访问的变量。

### 过滤器
Airflow 定义了一些可用于格式化值的 Jinja 过滤器。

### 宏指令
* datetime_diff_for_humans
* ds_add
* ds_format
* random
* closest_ds_partition
* max_partition

## Python API
### DAGs
DAG 是 Airflow 的核心模型，代表了循环工作流。
### Operators
运算符允许生成特定类型的任务，这些任务在实例化时成为 DAG 中的节点。 所有运算符都派生自 BaseOperator 并以这种方式继承许多属性和方法。有 3 种主要类型的运算符: 1, 执行操作的运算符，或告诉另一个系统执行操作. 2, 传输操作员将数据从一个系统移动到另一个系统. 3, 传感器是一种特定类型的运算符，它将一直运行直到满足特定条件。
* BaseOperator: 所有运算符都派生自 BaseOperator 并通过继承获得许多功能。
* BaseSensorOperator: 所有传感器都派生自 BaseSensorOperator。 所有传感器都在 BaseOperator 属性之上继承 timeout 和 poke_interval。
* Operators packages: 所有运算符都在以下包中：[airflow.operators](https://airflow.apache.org/docs/apache-airflow/2.2.5/_api/airflow/operators/index.html) [airflow.sensors](https://airflow.apache.org/docs/apache-airflow/2.2.5/_api/airflow/sensors/index.html)
### Hooks
挂钩是与外部平台和数据库的接口，在可能的情况下实现通用接口，并充当操作员的构建块。 所有的钩子都派生自 BaseHook。
* Hooks packages: [airflow.hooks](https://airflow.apache.org/docs/apache-airflow/2.2.5/_api/airflow/hooks/index.html)
### Executors
执行器是任务实例运行的机制。 所有的executor都派生自BaseExecutor。
* Executors packages: [airflow.executors](https://airflow.apache.org/docs/apache-airflow/2.2.5/_api/airflow/executors/index.html)
### Models
模型建立在 SQLAlchemy ORM 基类之上，实例保存在数据库中。[airflow.models](https://airflow.apache.org/docs/apache-airflow/2.2.5/_api/airflow/models/index.html)
### Exceptions
[Exceptions](https://airflow.apache.org/docs/apache-airflow/2.2.5/_api/airflow/exceptions/index.html)
### Secrets Backends
Airflow 依靠秘密后端来检索 Connection 对象。 所有秘密后端都派生自 BaseSecretsBackend。[airflow.secrets](https://airflow.apache.org/docs/apache-airflow/2.2.5/_api/airflow/secrets/index.html)
### Timetables
自定义时间表实现为 Airflow 的调度程序提供了额外的逻辑，以使用内置调度表达式无法实现的方式调度 DAG 运行。[airflow.timetables](https://airflow.apache.org/docs/apache-airflow/2.2.5/_api/airflow/timetables/index.html)

## 稳定的 REST API
## 弃用的 REST API
## 配置
此页面包含您可以在 airflow.cfg 文件中或使用环境变量设置的所有可用 Airflow [配置的列表](https://airflow.apache.org/docs/apache-airflow/2.2.5/configurations-ref.html)。

## 额外套餐
这是 Apache Airflow 的所有[额外依赖项](https://airflow.apache.org/docs/apache-airflow/2.2.5/extra-packages-ref.html)的列表。
## 数据库迁移