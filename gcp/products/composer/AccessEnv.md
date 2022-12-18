# 访问 Airflow 命令行界面
Apache Airflow 具有命令行界面 (CLI)，可用于执行任务，例如触发和管理 DAG、获取有关 DAG 运行和任务的信息、添加和删除连接和用户。
## CLI 语法版本简介
Cloud Composer 2 中的 Airflow 使用 [Airflow 2 CLI 语法](https://airflow.apache.org/docs/apache-airflow/stable/cli-and-env-variables-ref.html)
## 准备工作
您必须拥有将 gcloud 命令行工具与 Cloud Composer 搭配使用的足够权限。
## 运行 Airflow CLI 命令
* 子命令参数分隔符: 使用 **--** 分隔指定的 Airflow CLI 命令的参数.
* 默认位置
* 示例
* 在专用 IP 环境中运行命令
* 支持的 Airflow CLI 命令

# 访问 Airflow 网页界面
Apache Airflow 包含一个网页界面，可用于管理工作流 (DAG)、管理 Airflow 环境以及执行管理操作。
## Airflow Web 服务器
每个 Cloud Composer 环境都有一个 Web 服务器，用于运行 Airflow 网页界面。
### 重启网络服务器
调试或排查 Cloud Composer 环境时，部分问题可以通过重启 Airflow Web 服务器来解决。您可以使用 restartWebServer API 或 restart-web-server gcloud 命令重启 Web 服务器.
## 准备工作
## 访问网页界面
### 从 Google Cloud Console 访问网页界面
### 限制对 Airflow Web 服务器的访问
### 通过 gcloud 命令行工具检索网页界面网址

# 访问 Airflow REST API
Apache Airflow 具有一个 REST API 接口，可用于执行诸如以下任务：获取有关 DAG 运行和任务的信息、更新 DAG、获取 Airflow 配置、添加和删除连接以及列出用户。
## Airflow REST API 版本
## 准备工作
## 启用稳定的 Airflow REST API
## 启用实验性 Airflow REST API
## 允许使用 Webserver 访问权限控制对 Airflow REST API 进行 API 调用
## 调用 Airflow REST API
## 使用服务帐号访问 Airflow REST API
## 扩缩 Airflow REST API 组件

# 访问 Airflow 数据库
*本页面介绍如何连接到运行您的 Cloud Composer 环境的 Airflow 数据库的 Cloud SQL 实例以及如何运行 SQL 查询。对于 Cloud Composer 环境，一种方法是从环境的 GKE 集群中的虚拟机连接到 Airflow 数据库。
## 获取环境集群的名称和可用区
## 获取数据库连接参数
## 获取数据库端点地址
## 创建虚拟机实例
## 连接到虚拟机实例并安装 SQL 客户端软件包
## 转储数据库内容并转移到存储桶