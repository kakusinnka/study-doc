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

# 指定维护窗口
## 关于维护窗口
借助维护期，您可以控制环境的维护时间段：
* 如果您为环境定义了自定义维护窗口，则 Cloud Composer 会在这些定义的时间段内执行维护。
* 如果您没有为环境定义自定义维护期，则 Cloud Composer 会在默认维护期执行维护。
## 维护窗口期间会发生什么
指定维护窗口时，您在一周内为维护操作提供至少 12 小时的时间：
* 在维护期间，您的环境将保持可用。在进行维护操作时，环境中的部分组件可能会暂时不可用。
* 为保证 Cloud Composer 有足够的时间来安排和执行所有维护操作，您必须提供这 12 小时的时间。
## 默认维护窗口
默认情况下，维护窗口的运行时间为星期日、星期五和星期六的 00:00:00 到 04:00:00 (GMT)。
## 如何使用维护窗口
维护操作可能会影响 DAG 和 Airflow 任务的执行，因此我们建议您执行以下操作：
1. 定义 Cloud Composer 环境的维护窗口。
2. 通过在 DAG 中使用 start_date 和 schedule_interval 参数，安排在指定维护窗口之外运行的 DAG。
## 为新环境指定维护窗口
您可以在创建环境时指定维护窗口。
## 为现有环境指定维护窗口

# 配置电子邮件通知
## 准备工作
## 配置 SendGrid 电子邮件服务
要接收通知，请配置您的环境变量以通过 SendGrid 电子邮件服务发送电子邮件。
### 使用 SendGrid 注册
### 配置变量
* 在 Secret Manager 中存储值:  1, 安装 apache-airflow-providers-sendgrid PyPI 包。2, 确保为机密后端设置权限和 Airflow 配置选项。 先放一放。
* 使用环境变量设置值: 为您的环境设置以下环境变量
* 测试您的 SendGrid 配置
```
import datetime

import airflow
from airflow.operators.email import EmailOperator


with airflow.DAG(
    "composer_sample_sendgrid",
    start_date=datetime.datetime(2022, 1, 1),
) as dag:

    task_email = EmailOperator(
        task_id="send-email",
        conn_id="sendgrid_default",
        # You can specify more than one recipient with a list.
        to="user@example.com",
        subject="EmailOperator test for SendGrid",
        html_content="This is a test message sent through SendGrid.",
        dag=dag,
    )
```

# 管理环境标签并细分环境费用
为 Cloud Composer 环境分配标签，然后根据这些标签细分结算费用。

## 环境标签简介
环境标签是您可以分配给环境的键值对。每个环境可以有多个标签，但单个环境的标签键必须是唯一的。您可以为多个环境分配相同的键和值。

## 结算报告中的环境标签
您分配给环境的环境标签会在结算报告中显示，因此您可以根据标签中的键和值来细分费用。

## 为新环境分配标签
## 为现有环境分配标签
## 查看报告中的标签