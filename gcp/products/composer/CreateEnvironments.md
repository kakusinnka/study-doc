# 创建环境
Cloud Composer 环境是一个独立的 Apache Airflow 安装，部署到托管的 Google Kubernetes Engine 集群中。
## 准备工作
## 第 1 步：基本设置
此步骤会在指定位置创建一个使用默认参数的环境。
## 第 2 步：（可选）为您的环境选择服务帐号
Cloud Composer 将此 服务帐户 绑定到您环境的 Kubernetes 服务帐户。环境集群中的节点作为 Kubernetes 服务帐户运行并使用绑定的 服务帐户 访问您的 Google Cloud 项目中的资源。
## 第 3 步：向 Cloud Composer 服务帐号授予所需权限
当您在项目中启用 Cloud Composer API 时，会在您的项目中创建 Composer Service Agent 帐户。 Cloud Composer 使用此帐号在您的 Google Cloud 项目中执行操作。
## 第 4 步：（可选）配置环境规模和性能参数
如需为您的环境指定扩缩和性能配置，请选择环境大小和工作负载配置。在 Cloud Composer 2 中，您可以在创建环境后更改所有性能和扩缩参数。
### 环境大小
控制托管 Cloud Composer 基础架构的性能参数, 包括 Airflow 数据库。
### 工作负载配置
控制 "在 GKE 集群中运行的" 环境组件 (Airflow schedulers, Airflow web server, and Airflow workers.) 的规模和性能
* Airflow 调度器: 解析 DAG 定义文件，根据调度间隔安排 DAG 运行，并将任务加入 Airflow 工作器执行队列。
* Airflow 触发器: 异步监控您的环境中的所有延迟任务。
* Airflow Web 服务器: 运行 Airflow 网页界面，您可以在其中监控、管理和直观呈现 DAG。
* Airflow 工作器: 执行由 Airflow 调度器执行的任务。环境中的工作器数量下限和上限会动态变化，具体取决于队列中的任务数量。
## 第 5 步：（可选）配置环境的网络
## 第 6 步：（可选）配置网络服务器网络访问权限
Airflow 网络服务器访问参数不取决于您的环境类型。您可以改为单独配置网络服务器访问权限。例如，专用 IP 环境仍然可以通过互联网访问 Airflow 界面。
## 第 7 步：（可选）指定 Airflow 配置替换和环境变量
您可以在创建环境时设置 Airflow 配置替换和环境变量。或者，您可以在创建环境后执行此操作。某些 Airflow 配置选项被屏蔽，您无法替换这些选项。
## 第 8 步：（可选）指定维护窗口
## 第 9 步：（可选）配置数据加密 (CMEK)
默认情况下，环境中的数据使用 Google 提供的密钥进行加密。如需使用客户管理的加密密钥 (CMEK) 来加密您环境中的数据，请按照 [使用客户管理的加密密钥](https://cloud.google.com/composer/docs/composer-2/configure-cmek-encryption) 中的说明操作。
## 第 10 步：（可选）指定环境标签
您可以为环境分配标签，以根据标签细分结算费用。