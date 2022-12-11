# 设置环境变量
Cloud Composer 使用环境变量来更改 Airflow 或 DAG 的运行时行为。环境变量具有持久性。您指定一个环境变量后，Airflow 会一直使用它，直到您从环境中移除该变量。  
Cloud Composer 不使用环境变量来配置 Airflow。 使用 **Airflow 配置覆盖** 来配置 Airflow。
## Name format
## 为新环境设置环境变量
您可以在创建环境时指定环境变量。
## 为现有环境设置环境变量

# 替换 Airflow 配置选项
替换新环境和现有环境的 Airflow 配置选项。创建或更新环境时，您可以使用不同的值替换 Apache Airflow 配置选项。这样，您便可以根据自己的需求和要求调整 Airflow 实例。
## 替换新环境的 Airflow 配置选项
## 替换现有环境的 Airflow 配置选项

# 扩缩环境
## 纵向和横向扩缩
* 横向扩缩选项：
  * 调整工作器数量的下限和上限
  * 调整调度器的数量
  * 启用触发器
* 纵向扩缩选项：
  * 调整工作器、调度器、触发器和网络服务器规模及性能参数
  * 调整环境大小

## 调整工作器数量的下限和上限
您可以为环境设置工作器数量下限和上限。环境中的工作器数量会根据队列中的任务数量动态变化。 Cloud Composer 会在设定的限制内自动扩缩您的环境。您可以随时调整这些限制。
## 调整调度器的数量
您的环境可以同时运行多个 Airflow 调度器。使用多个调度器在多个调度器实例之间分配负载，以实现更好的性能和可靠性。您可以指定调度器数量，不超过您环境中的节点数。
## 启用触发器
通过启用 Airflow 触发器，您可以在 DAG 中使用可延期运算符。 详细了解 [如何使用可延期运算符](https://cloud.google.com/composer/docs/composer-2/use-deferrable-operators)。
## 调整工作器、调度器、触发器和网络服务器规模及性能参数
您可以指定您的环境所使用的 CPU 数量、内存和磁盘空间大小。通过这种方式，除了使用多个工作器和调度器进行横向扩缩之外，您还可以提高您的环境的性能。
## 调整环境大小
环境大小用于控制包含 Airflow 数据库的代管式 Cloud Composer 基础架构的性能参数。如果要运行大量 DAG 和任务，请考虑选择较大的环境大小。

# 管理 Airflow 连接
Airflow 连接可让您从 Cloud Composer 环境访问 Google Cloud 项目中的资源。您可创建 Airflow 连接 ID 来存储信息（例如登录名和主机名），并且您的工作流会引用连接 ID。推荐使用 Airflow 连接来存储工作流中使用的密钥和凭据。
## Fernet 密钥和安全连接
创建新环境时，Cloud Composer 会为该环境生成一个唯一的永久性 Fernet 密钥，并默认保护连接额外服务。您可以在 Airflow 配置中查看 fernet_key。
## 使用默认连接
默认情况下，Cloud Composer 会为 Google Cloud Platform 配置 [默认 Airflow 连接](https://airflow.apache.org/docs/apache-airflow-providers-google/stable/connections/index.html)。 您可以使用默认连接 ID 在 DAG 中使用这些连接。您也可以在创建运算符时显式指定连接 ID。
## 访问其他项目中的资源
要让 Cloud Composer 环境访问 Google Cloud 项目中的资源，推荐的方法是使用默认连接以及为与您的环境关联的服务帐号分配适当的 Identity and Access Management 权限。
* 确定与您的环境相关联的服务帐号
* 向服务帐号授予适当的 IAM 权限
## 创建新的 Airflow 连接
* 准备工作: 向与您的 Cloud Composer 环境关联的服务帐号授予适当的 IAM 权限，并使用 DAG 定义中的默认连接。
* 创建与其他项目的连接: 要使用您创建的连接，请在构建 Google Cloud Airflow 操作器时将其设置为相应的连接 ID 参数。