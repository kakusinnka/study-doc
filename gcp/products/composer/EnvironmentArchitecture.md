# Cloud Composer 环境架构
## 环境架构配置
## 客户和租户项目
当您创建环境时，Cloud Composer 会在租户和客户项目之间分配环境的资源。

## 环境组件
环境组件是作为环境的一部分在 Google Cloud 上运行的代管式 Airflow 基础架构的一个元素。
### 环境的集群
环境的集群是环境的 Autopilot 模式 VPC 原生 Google Kubernetes Engine 集群
### Airflow 调度器、触发器、工作器和 Redis 队列
* Airflow 调度器: 控制 DAG 运行和 DAG 中各项任务的时间安排。
* Airflow 工作器: 通过从 Redis 队列获取 DAG 中的各项任务来执行任务。
* Airflow 触发器: 异步监控您的环境中的所有延迟任务。
### Airflow Web 服务器
Airflow Web 服务器用于运行环境的 Airflow 界面。
### Airflow 数据库
Airflow 数据库是您的环境的租户项目中运行的 Cloud SQL 实例。
### 环境存储桶
环境存储桶是一个 Cloud Storage 存储桶，用于存储 DAG、插件、数据依赖项和 Airflow 日志。
### 其他环境组件
* Cloud SQL Storage: 存储 Airflow 数据库备份。
* Cloud SQL 代理: 将环境的其他组件连接到 Airflow 数据库。
* Airflow 监控: 向 Cloud Monitoring 报告环境指标并触发 airflow_monitoring DAG。
* Composer 代理可执行环境操作，例如创建、更新、升级和删除环境。
* Airflow InitDB 可创建一个 Cloud SQL 实例和初始数据库架构。
* FluentD。从所有环境组件收集日志，并将日志上传到 Cloud Logging。
* Pub/Sub 订阅。您的环境通过 Pub/Sub 订阅与其 GKE 服务代理进行通信。
* PSC 端点将 Airflow 调度器和工作器连接到具有 PSC 的专用 IP 架构中的 Airflow 数据库。
* 客户指标 Stackdriver 适配器会报告环境的指标，以便进行自动扩缩。
* Airflow 工作器设置控制器会根据客户指标 Stackdriver 适配器中的指标自动扩缩您的环境。
* Cloud Storage FUSE: 将环境的存储桶作为文件系统装载到 Airflow 工作器、调度器和 Web 服务器上，以便这些组件可以访问该存储桶中的数据。
### 公共 IP 环境架构
### 专用 IP
### 与 Cloud Logging 和 Cloud Monitoring 集成
Cloud Composer 集成了您的 Google Cloud 项目的 Cloud Logging 和 Cloud Monitoring，因此您可以集中查看 Airflow 服务和工作流日志。
