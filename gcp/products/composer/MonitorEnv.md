# 查看 Airflow 日志
## 日志类型
* Airflow 日志：这类日志与单一 DAG 任务关联。您可以在与 Cloud Composer 环境关联的 Cloud Storage logs 文件夹中查看任务日志，还可以在 Airflow 网页界面中查看日志。
* 流日志：这类日志是 Airflow 中日志的超集。如需访问流式传输日志，您可以转到 Google Cloud Console 中“环境详情”页面的“日志”标签页，使用 Cloud Logging 或使用 Cloud Monitoring。
## 登录 Cloud Storage
### 日志文件夹目录结构
### 日志保留
为了防止数据丢失，在您删除环境后，保存在 Cloud Storage 中的日志仍会保留。您必须手动从 Cloud Storage 删除这些日志。
## 准备工作
## 查看 Cloud Storage 中的任务日志
## 在 Google Cloud Console 中查看流式日志
可以在“环境详情”页面的“日志”标签页或在 Cloud Logging 中查看这些日志。

# 查看审核日志
## 概览
Google Cloud 服务会写入审核日志，便于您了解在您的 Google Cloud 资源中“谁在何时何地执行了什么操作”。
## 可用的审核日志
Cloud Composer 提供以下类型的审核日志：管理员活动审核日志，数据访问审核日志。
## 审核的操作
## 审核日志格式
### 日志名称
### 服务名称
### 资源类型
## 启用审核日志记录
## 权限和角色
## 查看日志
## 路由审核日志

# 使用 Monitoring 信息中心
访问和使用 Cloud Composer 环境的监控信息中心。此信息中心包含指标和图表，用于监控环境中运行的 DAG 的趋势，以及识别 Airflow 组件和 Cloud Composer 资源的问题。
## 访问监控信息中心
## 选择时间范围
## 设置提醒
## 在 Monitoring 中查看指标
## 指标说明
### 环境概览
### Airflow 组件
### DAG 运行
### DAG 解析时间和 DAG 执行时间之间的区别

# 使用 Cloud Monitoring 监控环境
您可以将 Cloud Monitoring 和 Cloud Logging 与 Cloud Composer 搭配使用。
## 环境指标
### 环境健康状况
### 数据库健康状况
### 数据库指标
### 工作器指标
### 网络服务器指标
### DAG 指标
### Celery Executor 指标
### Airflow 指标
## 将 Monitoring 用于 Cloud Composer 环境
## 使用 Cloud Monitoring 提醒