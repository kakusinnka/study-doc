# 概述
Cloud Composer 是一项代管式 Apache Airflow 服务，可帮助您创建、安排、监控和管理工作流。借助 Cloud Composer 自动化功能，您可以快速创建 Airflow 环境，并使用 Airflow 原生工具（例如功能强大的 Airflow 网页界面和命令行工具），从而全力专注于工作流，而无需管理基础架构。

# Cloud Composer 2 指南
## 快速入门
Quickstart.md

# 方法指南
## 所有方法指南

## 启用和停用 Cloud Composer 服务
停用 Cloud Composer API 后，项目中的环境将无法恢复。停用 API 后，您仍然可以访问存储在环境存储桶中的数据，但环境本身不再可用。

## 创建环境
CreateEnvironments.md

## 使用 Terraform 创建环境
Terraform 待学习

## 优化环境性能和费用
OptimizeEnvPerformanceCost.md

## 运行本地 Airflow 环境
RunLocalAirflowEnv.md

## 配置网络
先不看

## 配置环境
ConfigEnv.md

## 配置安全性和访问权限控制
先放一放

## 更新、升级和删除环境
ChangeEnv.md

## 访问环境
AccessEnv.md

## 管理 DAGs
MngDag.md

## 监控环境
MonitorEnv.md

## 使用 Dataplex 的数据沿袭
先放一放

# 问题排查
先放一放

# 概念
## 所有概念
## Cloud Composer 概览
ComposerOverview.md

## Cloud Composer 特性
ComposerFeatures.md

## Cloud Composer 版本控制概览
ComposerVersioning.md

## Cloud Composer 安全概览
* 基本的安全功能。介绍 Cloud Composer 环境中默认可用的功能。
* 高级安全功能。介绍可用于修改 Cloud Composer 以满足安全要求的功能。
* 标准遵从。提供 Cloud Composer 需要符合的标准列表。
先放一放

## Cloud Composer 环境架构
EnvironmentArchitecture.md

## 环境扩缩
### 自动扩缩环境
Cloud Composer 2 环境会自动根据执行的 DAG 和任务的需求进行扩缩
### 规模和性能参数
除了自动扩缩之外，您还可以通过调整调度器、网络服务器和工作器的 CPU、内存和磁盘限制来控制环境的规模和性能参数。这样，除了自动扩缩功能提供的横向扩缩之外，您还可以纵向扩缩环境。您可以随时调整 Airflow 调度器、网络服务器和工作器的扩缩与性能参数。
### 多个调度器
Airflow 2 可以同时使用多个 Airflow 调度器。
### 数据库磁盘空间
Airflow 数据库的磁盘空间会自动增加以满足需求。

## 专用 IP 环境
### VPC 原生 GKE 集群
### 专用 IP Cloud Composer 环境
您可以在创建环境时选择专用 IP 环境。使用专用 IP 意味着环境中的 GKE 和 Cloud SQL 虚拟机不会被分配公共 IP 地址，并且只能通过 Google 的内部网络进行通信。使用专用 IP 不会影响您通过公共 IP 访问 Cloud Storage 或 Airflow Web 服务器的方式。
* GKE 集群
* Cloud SQL
* 为工作流开放公共互联网访问权限

## Cloud Composer 身份验证概览
### 支持的身份验证方法
* 服务帐号
* 用户帐号
### 访问权限控制

## 存储在 Cloud Storage 中的数据
### Cloud Storage 存储桶中的文件夹
### 容量注意事项
* DAG 和插件
### 数据
* 日志
* Webserver、dags/、plugins/ 和 data/ 文件夹***
### 数据同步
* Cloud Composer 1 与 Cloud Composer 2 之间的区别

## 受支持的 Python 版本
## Cloud Composer 与 Workflows 比较
