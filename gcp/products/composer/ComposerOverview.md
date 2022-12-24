# Cloud Composer 概览
Cloud Composer 是一项全代管式工作流编排服务，在常用的 Apache Airflow 开源项目的基础上构建而成，用户无需管理基础架构。
## 工作流、DAG 和任务
* 工作流: 在数据分析中，工作流表示用于提取、转换、分析或利用数据的一系列任务。
* DAG: 安排和运行的任务的集合.
* 任务: 任务可以表示几乎任何事物, 
> DAG 不应该关注每个组成任务的功能，其用途是确保每项任务在正确的时间、以正确的顺序执行，或处理的是正确的问题。
## Cloud Composer 环境
如需运行工作流，首先需要创建一个环境。Airflow 依赖于许多微服务来运行，因此 Cloud Composer 会预配 Google Cloud 组件来运行工作流。这些组件统称为 Cloud Composer 环境。
## Cloud Composer 使用哪个版本的 Apache Airflow？
每个 Cloud Composer 版本都支持多个 Apache Airflow 版本。
## 我可以使用 Airflow 原生界面和 CLI 吗？
如需在您的环境中运行 Airflow CLI 命令，请使用 gcloud 命令。
## 我可以将自己的数据库用作 Airflow 元数据数据库吗？
您无法将用户提供的数据库用作 Airflow 元数据数据库。
## 我可以将自己的集群用作 Cloud Composer 集群吗？
无法基于自行管理的 Google Kubernetes Engine 集群构建 Cloud Composer 环境。
## 我可以使用自己的 Container Registry 吗？
您无法将其替换为用户提供的 Container Registry。
## Cloud Composer 环境是可用 zonal 级还是 regional 级？
* Cloud Composer 1 环境为可用 zonal 级环境。
* Cloud Composer 2 环境有一个可用 zonal 级 Airflow 元数据数据库和一个 regional 级 Airflow 调度和执行层。