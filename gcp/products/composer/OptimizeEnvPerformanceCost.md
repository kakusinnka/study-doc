# 优化环境性能和费用
本页介绍如何根据项目的需求调整环境的规模和性能参数，以便提高性能并降低环境未使用的资源费用。
## 优化过程概览
更改环境参数可能会影响环境性能的许多方面。我们建议您在迭代中优化您的环境：
1. 从环境预设开始。
2. 运行您的 DAG。
3. 观察环境的性能。
4. 调整环境规模和性能参数，然后重复上一步。

## 从环境预设开始
在 Google Cloud 控制台中创建环境时，您可以从三种环境预设中选择一种。这些预设设置环境的初始规模和性能配置：创建环境后，您可以更改预设提供的所有规模和性能参数。

## 运行您的 DAG
创建环境后，将您的 DAG 上传到该环境。运行您的 DAG 并观察环境的性能。

## 观察环境的性能
本部分重点介绍最常见的 Cloud Composer 2 容量和性能优化方面。我们建议逐步按照本指南操作，因为本指南会首先介绍最常见的性能考虑因素。
### 转到 Monitoring 信息中心
### 监控调度器 CPU 和内存指标
Airflow 调度器的 CPU 和内存指标可帮助您检查调度器的性能是否是 Airflow 整体性能的瓶颈。
### 监控所有 DAG 文件的总解析时间
调度器会在安排 DAG 运行之前解析 DAG。如果 DAG 需要很长时间才能解析，这会占用调度器的容量，并且可能会降低 DAG 运行的性能。
### 监控工作器 pod 逐出
当环境集群中的特定 pod 达到其资源限制时，可能会发生 pod 逐出。如果 Airflow 工作器 pod 被逐出，则该 pod 上运行的所有任务实例都会中断，之后被 Airflow 标记为失败。工作器 pod 逐出的大多数问题都是因为工作器中出现内存不足的情况导致的。
### 监控活跃工作器数
您的环境中的工作器数量会自动根据队列中的任务进行扩缩。
### 监控工作器的 CPU 和内存用量
监控环境中所有工作器的 CPU 总使用率和内存总用量，以确定 Airflow 工作器是否适当地使用了环境的资源。
### 监控正在运行和已加入队列的任务数
您可以监控已加入队列和正在运行的任务数量，以检查调度过程的效率。
### 监控数据库 CPU 和内存用量
Airflow 数据库性能问题可能会导致整体 DAG 执行问题。数据库磁盘使用量通常不是问题的根源，因为存储空间会根据需要自动扩展。
### 监控任务调度延迟时间
如果任务之间的延迟时间超过预期水平（例如，20 秒或更长），则可能表示环境无法处理由 DAG 运行生成的任务负载。
### 监控网络服务器 CPU 和内存
Airflow 网络服务器性能会影响 Airflow 界面。网络服务器过载的情况不常见。如果发生这种情况，Airflow 界面性能可能会降低，但这不会影响 DAG 运行的性能。

## 调整环境的规模和性能参数
* [更改调度器的数量](https://cloud.google.com/composer/docs/composer-2/scale-environments?hl=zh-cn#scheduler-count) : 调整调度器的数量可提高调度器的容量并增强 Airflow 调度的弹性。
* [更改调度器的 CPU 和内存](https://cloud.google.com/composer/docs/composer-2/scale-environments?hl=zh-cn#workloads-configuration) : CPU 和内存参数适用于环境中的每个调度器。

## 更改工作器数量上限
增加工作器数量上限后，您的环境即可根据需要自动扩充更多工作器。减少工作器数量上限会降低环境的最大容量，但也可能会有助于降低环境费用。按照 [调整工作器数量下限和上限](https://cloud.google.com/composer/docs/composer-2/scale-environments?hl=zh-cn#autoscaling-workers) 中的步骤设置环境所需的工作器数量上限。

## 更改工作器 CPU 和内存
* 更改工作器 CPU 或内存会重启工作器，这可能会影响正在运行的任务。我们建议在没有运行 DAG 时执行此操作。
* CPU 和内存参数属于环境中的每个工作器。例如，如果您的环境有四个工作器，则总容量是 CPU 和内存指定量的四倍。
* 按照 [调整工作器、调度器和网络服务器的规模和性能参数](https://cloud.google.com/composer/docs/composer-2/scale-environments?hl=zh-cn#workloads-configuration) 中的步骤，为工作器设置 CPU 和内存。

## 更改网络服务器的 CPU 和内存
当网络服务器用量图表指示网络服务器 CPU 或内存利用率持续过低时，减少该网络服务器的 CPU 或内存会很有帮助。更改网络服务器参数会重启网络服务器，这会导致网络服务器临时停机。我们建议您在常规使用时段之外进行更改。
* 按照 [调整工作器、调度器和网络服务器的规模和性能参数](https://cloud.google.com/composer/docs/composer-2/scale-environments?hl=zh-cn#workloads-configuration) 中的步骤，为网络服务器设置 CPU 和内存。

## 更改环境大小
更改环境大小会修改 Cloud Composer 后端组件（例如 Airflow 数据库和 Airflow 队列）的容量。
* 按照 [调整环境大小](https://cloud.google.com/composer/docs/composer-2/scale-environments?hl=zh-cn#environment-size) 中的步骤设置环境大小。

## 更改 DAG 目录列举间隔
增加 DAG 目录列表间隔可减少与在环境存储桶中发现新 DAG 相关的调度程序负载。
* 如需更改此参数，请 [替换 Airflow 配置](https://cloud.google.com/composer/docs/composer-2/override-airflow-configurations?hl=zh-cn) 选项

## 更改 DAG 文件解析间隔
增加 DAG 文件解析间隔可减少与 DAG 包中的 DAG 连续解析相关的调度程序负载。
* 如需更改此参数，请 [替换 Airflow 配置](https://cloud.google.com/composer/docs/composer-2/override-airflow-configurations?hl=zh-cn) 选项

## 工作器并发
并发性能和环境的自动扩缩能力与以下两项设置相关联: 
* Airflow 工作器数量下限
* [celery] worker_concurrency 参数
### 工作器并发性能注意事项
[celery] worker_concurrency 参数定义了单个工作器可以从任务队列中选取的任务数量。任务执行速度取决于多种因素，例如工作器 CPU、内存和工作本身的类型。
* 工作器自动扩缩: Cloud Composer 会监控任务队列，并产生额外的工作器来选择所有等待的任务。将 [celery] worker_concurrency 设置为较高值意味着每个工作器都可以处理大量任务，因此在某些情况下，队列可能永远无法填满，从而导致自动扩缩永远无法触发。
* 任务日志同步: Airflow 工作器具有可将任务执行日志同步到 Cloud Storage 存储分区的组件。如果单个工作器执行大量并发任务，则可能会导致大量同步请求。 这可能会导致您的工作器过载，并导致性能问题。如果您由于大量日志同步流量而观察到性能问题，请降低 [celery] worker_concurrency 值，并调整 Airflow 工作器的最小数量。
### 更改工作器并发数
更改此参数可调整单个工作器可以同时执行的任务量。

## 更改 DAG 并发数
DAG 并发数定义了每个 DAG 中可以同时运行的任务实例数上限。如果 DAG 运行大量并发任务，请增大此值。如果此设置较低，则调度器会延迟将更多任务放入队列，从而降低环境自动扩缩的效率。

## 提高每个 DAG 的活跃运行数上限
此属性定义每个 DAG 的活跃 DAG 运行次数上限。如果同一 DAG 必须并发运行多次（例如，使用不同的输入参数），则此属性允许调度器并行启动此类运行。