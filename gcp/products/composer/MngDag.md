# 查看 DAG、 DAG 运行和任务
DAG 界面是 Cloud Composer 控制台界面的一部分，专门用于查看和监控 DAG、DAG 运行以及各个任务。
## 查看 DAG 相关信息的方法
## 关于 Cloud Composer DAG 界面
## 准备工作
## 查看您的环境的 DAG 列表
## 查看 DAG 运行和任务的历史记录
## 查看 DAG 图
## 查看 DAG 源代码以及 DAG 的其他信息

# 添加和更新 DAG
Cloud Composer 使用 Cloud Storage 存储桶来存储 Cloud Composer 环境的 DAG。您的环境会将此存储桶中的 DAG 同步到 Airflow 工作器和调度器等 Airflow 组件。
## 准备工作
* 由于 Apache Airflow 不提供强大的 DAG 隔离功能，建议您分开维护生产环境和测试环境，以防止产生 DAG 干扰。
* DAG 的更改会在 3-5 分钟内传播到 Airflow。
## 访问环境的存储桶
## 添加或更新 DAG
### 更新具有活跃 DAG 运行作业的 DAG
如果您更新具有活跃 DAG 运行作业的 DAG：
* 所有当前正在执行的任务都会使用原始 DAG 文件继续运行。
* 已安排但尚未运行的所有任务都会使用更新后的 DAG 文件。
* 更新后的 DAG 文件中不再存在的所有任务都会标记为已移除。
### 更新频繁运行的 DAG

## 删除 DAG
### 在您的环境中删除 DAG
> 删除 DAG 不会从 Airflow 界面中移除 DAG 元数据。
### 从 Airflow 界面中移除 DAG

# 触发 DAG
## Airflow 提供以下触发 DAG 的方法：
* 按时间表触发。创建 DAG 时，您需要为它指定时间表。Airflow 会根据指定的时间安排参数自动触发 DAG。
* 手动触发。您可以从 Airflow 界面手动触发 DAG，也可以从 gcloud 运行 Airflow CLI 命令来触发。
* 触发来响应事件。触发 DAG 来响应事件的标准方法是使用传感器。
## 触发 DAG 的其他方法：
* 以编程方式触发。您可以使用 Airflow REST API 触发 DAG。例如，从 Python 脚本。
* 以编程方式触发以响应事件。您可以使用 Cloud Functions 和 Airflow REST API 触发 DAG 来响应事件。
## 按计划触发 DAG
* 指定时间安排参数: 当您定义 DAG 时，在 schedule_interval 参数中指定您希望运行 DAG 的频率。在 start_date 参数中，指定您希望 Airflow 开始安排 DAG 的时间。DAG 中的任务可以有各自的开始日期，或者您可以为所有任务指定一个开始日期。Airflow 会根据 DAG 中任务的最早开始日期和计划的时间间隔安排 DAG 运行。
* 更多时间安排参数示例
## 手动触发 DAG
当您手动触发 DAG 时，Airflow 会执行一次 DAG 运行。例如，如果您有一个已按时间表运行的 DAG，并且手动触发此 DAG，则 Airflow 会执行一次 DAG，这与为 DAG 指定的实际时间表无关。

# 编写 DAG
## 构建 DAG
1. DAG 定义。
2. 操作器（用于描述要完成的任务）。一个运算符实例称为一项任务。
3. 任务关系，用于描述任务的完成顺序。
## 运算符
以下示例演示了几个常用的 Airflow 运算符。
### BashOperator
用于运行命令行程序。Cloud Composer 在工作器的 Bash 脚本中运行提供的命令。 工作器是一个基于 Debian 的 Docker 容器，其中包含多个软件包: gcloud, bq, gsutil, kubectl 命令。
### PythonOperator
用于运行任意 Python 代码。Cloud Composer 在一个容器中运行 Python 代码，其中包含您的环境中使用的 Cloud Composer 映像版本的软件包。如需安装其他 Python 软件包，请参阅[安装 Python 依赖项](https://cloud.google.com/composer/docs/composer-2/run-apache-airflow-dag?hl=zh-cn)。
### Google Cloud 运算符
Google Cloud Airflow 运算符用于运行使用 Google Cloud 产品的任务。Cloud Composer 会自动配置与环境项目之间的 Airflow 连接。
* BigQuery 运算符用于查询和处理 BigQuery 中的数据。
* Dataflow 运算符用于在 Dataflow 中运行 Apache Beam 作业。
* Cloud Data Fusion 运算符管理和运行 Cloud Data Fusion 流水线。
* Cloud Dataproc 运算符用于在 Dataproc 中运行 Hadoop 和 Spark 作业。
* Datastore 运算符用于在 Datastore 中读取和写入数据。
* AI Platform 运算符用于在 AI Platform 中运行训练和预测作业。
* Cloud Storage 运算符用于在 Cloud Storage 中读取和写入数据。
### EmailOperator
使用 EmailOperator 从 DAG 发送电子邮件。如需从 Cloud Composer 环境发送电子邮件，您必须将您的环境配置为使用 SendGrid。

## 通知
如果您希望在 DAG 中的运算符发生失败时发送电子邮件通知，可以将 email_on_failure 设置为 True。如需从 Cloud Composer 环境发送电子邮件通知，您必须将您的环境配置为使用 SendGrid。
## 指南
* Airflow 在扫描 dags/ 文件夹时，只会检查以下 Python 模块中的 DAG：位于 DAGs 文件夹顶层的 Python 模块，以及位于某一 ZIP 归档文件（该文件也位于顶层 dags/ 文件夹）顶层的 Python 模块。
* Airflow 任务可能会因多种原因而失败。为避免 DAG 运行失败，我们建议您启用任务重试功能。将重试次数上限设置为 0 表示不会执行任何重试操作。
* 限制 /dags 文件夹中的 DAG 文件数量

## 有关编写 DAG 的常见问题解答
* 如果我想在多个 DAG 中运行相同或类似的任务，如何尽量减少重复代码？
* 如何在 DAG 文件之间重复使用代码？
* 如何尽量降低出现不同定义的风险？
* 如何设置 DAG 之间的依赖项？
  * 如果您有两个 DAG（即 DAG A 和 DAG B），并且希望 DAG B 在 DAG A 之后触发，则可以在 DAG A 末尾添加一个 TriggerDagRunOperator
  * 如果 DAG B 仅依赖于 DAG A 生成的工件（例如 Pub/Sub 消息），那么可能更适合使用传感器。
* 如何将唯一运行 ID 传递给某一 DAG 及其任务？
* 如何在 DAG 中分离任务？
* 如果我需要汇总多个来源中的数据，那么是否应该在一个 DAG 中定义多项任务？
* 如何限制在一个 DAG 中运行的并发任务数量？
  * 您可以在 Airflow 网页界面中定义 Airflow 池，并将任务与 DAG 中的现有池相关联。
## 有关使用运算符的常见问题解答
* 我是否应该使用 DockerOperator？不推荐
* 我是否应该使用 SubDagOperator？不推荐
* 如果我想将 Python 运算符完全隔离，是否应该仅在 PythonOperators 中运行 Python 代码？
* 如何添加自定义二进制文件或非 PyPI 软件包？
* 如何将参数统一传递给某一 DAG 及其任务？
## 何时会发生模板替换
## 如何确定哪些运算符参数支持模板替换

# 在 DAG 中使用可延期运算符
## Cloud Composer 中的 Deferrable Operator 简介
## 准备工作
## 启用对可延期运算符的支持
## 在 DAG 中使用可延期运算符
## 查看触发器日志
## 监控触发器

# 使用 KubernetesPodOperator
先放一放
# 使用 Google Kubernetes Engine Operator
先放一放

# 将 DAG 中的任务分组
## 将 DAG 图中的任务分组
## 从父 DAG 触发子 DAG
* TriggerDagRunOperator
## 使用 TaskGroup operator 将任务分组
在 Airflow 2 中，您可以使用 TaskGroup operator 将 DAG 中的任务分组一起。在 TaskGroup 块中定义的任务仍然是主 DAG 的一部分。

# 使用 Cloud Functions 触发 DAG
Airflow 设计为定期运行 DAG，但您也可以通过响应事件来触发 DAG。方法之一是使用 Cloud Functions 在发生指定事件时触发 Cloud Composer DAG。例如，您可以创建一个函数，当 Cloud Storage 存储桶中的对象发生更改时或者当消息推送到 Pub/Sub 主题时触发 DAG。
## 允许使用 Webserver 访问控制对 Airflow REST API 进行 API 调用
## 创建 Cloud Storage 存储桶
## 部署触发 DAG 的 Cloud Functions 函数
先放一放

# 通过 Google Transfer Operator 从其他服务中转移数据
## Google 转移运营商简介
## 准备工作
## Amazon S3 到 Cloud Storage
### 安装 Amazon Provider 软件包
### 配置与 Amazon S3 的连接
### 从 Amazon S3 转移数据
## 从 Azure 文件共享到 Cloud Storage
### 安装 Microsoft Azure 提供方软件包
### 配置与 Azure FileShare 的连接
### 从 Azure FileShare 转移数据

# 使用 Cloud Composer 运行 Dataproc 无服务器工作负载
先放一放

# 使用 SSHOperator 连接到 Compute Engine 虚拟机
## 创建连接到 Compute Engine 虚拟机实例的 DAG

# 安装自定义插件
通过 Apache Airflow 的插件管理器，您可以编写自定义的内部 Apache Airflow 运算符、钩子、传感器或接口。
## 准备工作
## 安装插件
如需将自定义插件安装到您的 Cloud Composer 环境中，请将插件代码复制到 Cloud Composer 环境所关联的 Cloud Storage 存储桶中的 plugins 文件夹。
## 查看插件列表
## 删除插件
## 下载插件
## 排查插件问题

# 安装 Python 依赖项
预安装的 PyPI 软件包是包含在环境的 Cloud Composer 映像中的软件包。自定义 PyPI 软件包是除了预安装软件包之外您还可以在环境中安装的软件包。
## 管理 Python 软件包的选项 
## 准备工作
## 查看软件包列表
您可以用多种格式获取环境的软件包列表。
### 查看预安装的软件包
如需查看您的环境的预安装软件包列表，请参阅您的环境的 [Cloud Composer 映像的软件包列表](https://cloud.google.com/composer/docs/concepts/versioning/composer-versions)。
### 查看所有软件包
以下 gcloud CLI 命令为您环境中的 Airflow 工作器返回 python -m pip list 命令的结果。
```
gcloud beta composer environments list-packages \
    ENVIRONMENT_NAME \
    --location LOCATION
```
您可以使用 --tree 参数获取 python -m pipdeptree --warn 命令的结果。
### 查看自定义 PyPI 软件包

## 安装软件包
### 从 PyPI 安装软件包
### 从公共代码库安装
### 从 Artifact Registry 代码库安装
### 从私有代码库安装
### 安装本地 Python 库
### 使用依赖于共享对象库的软件包
## 在专用 IP 环境中安装软件包
### 具有公共互联网访问权限的专用 IP 环境
### 未连接到互联网的专用 IP 环境
### 在资源位置限制下安装到专用 IP 环境
### 将 VPC 依赖项安装到 VPC Service Controls 边界中的专用 IP 环境

# 测试 DAG
在将 DAG 部署到生产环境之前，您可以执行 Airflow CLI 子命令，以在执行 DAG 的同一上下文中解析 DAG 代码。
## 在创建 DAG 期间进行测试
您可以在本地运行单个任务实例并查看日志输出。通过查看输出，您可以检查语法和任务错误。在本地测试不会检查依赖项或向数据库传达状态。
### 创建测试目录
### 检查语法错误
### 检查任务错误
## 更新和测试已部署的 DAG
## 测试 DAG 的常见问题解答
### 如何在生产和测试环境中隔离 DAG 运行？
我们建议您保留单独的生产 Cloud Composer 环境和测试 Cloud Composer 环境，以防止测试 DAG 干扰生产 DAG。
### 如何从不同的 GitHub 分支运行集成测试时避免 DAG 干扰
使用唯一的任务名称以防止干扰。
### 使用 Airflow 进行集成测试的最佳做法是什么？
我们建议您使用专用环境进行 Airflow 集成测试。
### 如何与其他 DAG 贡献者高效协作？
每位贡献者都可以在 data/ 文件夹中有一个用于开发的子目录。
### 如何使部署环境和生产环境保持同步？