# 在 Cloud Composer 2 中运行 Apache Airflow DAG
本页面介绍如何在 Cloud Composer 2 中创建 Cloud Composer 环境并运行 Apache Airflow DAG。
## 准备工作
## 创建环境
## 查看环境详情
创建完环境后，您可以查看环境的信息，例如 Cloud Composer 版本、Airflow 网页界面的网址，以及 Cloud Storage 中的 DAGs 文件夹。
## 创建 DAG
Airflow DAG 是您要安排和运行的有序任务的集合。DAG 在标准 Python 文件中定义。
## 将 DAG 上传到 Cloud Storage
Cloud Composer 只会安排位于环境的 Cloud Storage 存储桶所含 /dags 文件夹中的 DAG。
## 在 Airflow 界面中查看 DAG
每个 Cloud Composer 环境都有一个 Web 服务器，用于运行 Airflow 网页界面。您可以通过 Airflow 网页界面管理 DAG。
## 在 Airflow 日志中查看任务实例详情
您还可以在 Google Cloud Console、环境的 Cloud Storage 存储桶和 Cloud Logging 中查看 Airflow 日志。