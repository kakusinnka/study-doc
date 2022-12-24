# Cloud Composer 特性
## Airflow 环境
Cloud Composer 环境是 Apache Airflow 的封装容器。Cloud Composer 会为每个环境创建以下组件: GKE 集群, Web 服务器, 数据库, Cloud Storage 存储桶.

## Airflow 管理
您可以使用以下 Airflow 原生工具来访问和管理 Airflow 环境:
* 网页界面
* 命令行工具: 安装 Google Cloud CLI 后，您可以运行 gcloud composer environments 命令来向 Cloud Composer 环境发出 Airflow 命令行命令。
* 除了原生工具之外，您还可以使用 Cloud Composer REST 和 RPC API 以编程方式访问您的 Airflow 环境。

## Airflow 配置
一般而言，Cloud Composer 为 Apache Airflow 提供的配置与本地托管的 Airflow 部署配置相同。部分 Airflow 配置已在 Cloud Composer 中预先配置，您无法更改这些配置属性。对于其他配置，您可以在创建或更新环境时加以指定。
### Airflow DAG（工作流）
Apache Airflow DAG 是一种工作流，其中包含一系列任务以及其他任务依赖项。
### 插件
您可以在 Cloud Composer 环境中安装自定义插件，例如自定义的内部 Apache Airflow 操作器、钩子、传感器或接口。
### Python 依赖项
您可以从环境中的 Python Package Index 或从私有软件包代码库安装 Python 依赖项。

## 访问权限控制
您可以管理 Google Cloud 项目级安全性，还可以分配 Identity and Access Management (IAM) 角色来阻止个别用户修改或创建环境。

## 日志记录和监控
您可以通过 Airflow 网页界面查看与个别 DAG 任务关联的 Airflow 日志，也可以在环境的 Cloud Storage 存储桶中查看 logs 文件夹。Cloud Composer 可提供流式日志。Cloud Composer 还可为您的 Google Cloud 项目提供审核日志，例如管理员活动审核日志。

## 网络和安全
默认情况下，Cloud Composer 会部署一个 Autopilot 模式 VPC 原生 Google Kubernetes Engine 集群。
### 共享 VPC
共享 VPC 可让您通过中央宿主项目管理共享网络资源，从而对各项目强制执行统一的网络政策。
### VPC 原生 Cloud Composer 环境
使用 VPC 原生功能时，GKE 集群中的 pod 和服务 IP 地址可在 Google Cloud 网络中进行原生路由，包括通过 VPC 网络对等互连。
### 专用 IP Cloud Composer 环境
使用专用 IP 时，Cloud Composer 工作流会与公共互联网完全隔离开来。

## 数据沿袭与 Dataplex 集成
数据沿袭是一项 Dataplex 功能，可让您跟踪数据在系统中的移动方式：数据的来源、传递位置以及对其进行的转换。