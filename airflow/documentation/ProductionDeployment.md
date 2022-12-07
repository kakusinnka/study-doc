# 生产部署
现在是在生产中部署 DAG 的时候了。

## 数据库后端
Airflow 默认带有 SQLite 后端。这允许用户在没有任何外部数据库的情况下运行 Airflow。但是，这样的设置仅用于测试目的；在生产中运行默认设置可能会导致多种情况下的数据丢失。如果要运行生产级 Airflow，请确保将后端配置为外部数据库，例如 PostgreSQL 或 MySQL。

## 多节点集群

## 日志
如果您在集群中使用一次性节点，请将日志存储配置为分布式文件系统 (DFS)，例如 S3 和 GCS，或外部服务，例如 Stackdriver Logging、Elasticsearch 或 Amazon CloudWatch。这样，即使在节点关闭或被替换后，日志仍然可用。

## 配置
您应该将环境变量用于跨部署更改的配置，例如元数据数据库、密码等。

## 调度程序正常运行时间
我们为 Apache Airflow 提供了一个 Docker 镜像 (OCI)，以便在容器化环境中使用。

## 生产容器镜像

## Kubernetes 的 Helm Chart
Helm提供了一种将软件部署到 Kubernetes 集群的简单机制。

## Kerberos 认证的工作人员

## Google Cloud 上的安全服务器和服务访问
本部分介绍在您的 Airflow 环境部署在 Google Cloud 上、连接到 Google 服务或连接到 Google API 时安全访问服务器和服务的技术和解决方案。
### IAM 和服务帐户
### 模拟服务帐户
### 访问计算引擎实例
### 访问亚马逊网络服务