# 任务
任务是 Airflow 中的基本执行单元。任务被安排到DAG中，然后在它们之间设置上游和下游依赖关系，以表达它们应该运行的顺序。

---
任务分为三种基本类型：
1. Operators，预定义的任务模板，您可以将它们快速串在一起以构建 DAG 的大部分。
2. Sensors， Operators 的一个特殊子类，它完全是关于等待外部事件发生的。
3. 一个 @task 修饰的 TaskFlow ，它是一个打包为任务的自定义 Python 函数。

在内部，这些实际上都是 Airflow 的 BaseOperator 的子类，Task 和 Operator 的概念在某种程度上可以互换，Operators 和 Sensors 是模板，当您在 DAG 文件中调用它们时，您就是在创建一个 Task 实例。

## 关系
使用任务的关键部分是定义它们如何相互关联 - 它们的依赖关系，或者它们的上游和下游任务。

## 任务实例
DAG 下的任务被实例化为 Task Instances (任务实例)运行。

---
任务实例的可能状态是：
* none: 该任务尚未排队等待执行
* scheduled: 调度程序已确定任务的依赖关系并且应该运行
* queued: 任务已分配给 Executor 并正在等待 worker
* running: 该任务正在运行
* success: 任务完成运行且没有错误
* shutdown: 任务运行时被外部请求关闭
* restarting: 任务运行时被外部请求重启
* failed: 任务在执行过程中出错，运行失败
* skipped: 任务被跳过
* upstream_failed: 上游任务失败
* up_for_retry: 任务失败，但还有重试次数，将重新安排
* up_for_reschedule: 该任务是一个 reschedule 模式的 Sensor
* sensing: 任务是 Smart Sensor (智能传感器)
* deferred: 该任务已推迟到触发器
* removed: 自运行开始后，该任务已从 DAG 中消失
![任务实例的可能状态](../../image/TaskInstancesStates.png)

---
关系术语

## 超时
如果您希望任务具有最大运行时间，请将其 execution_timeout 属性设置为最大允许运行时间的值。如果 execution_timeout 违反，则任务超时并引发 AirflowTaskTimeout 异常。此外，传感器还有一个 timeout 参数。这仅对 reschedule 模式下的传感器重要。timeout 控制允许传感器成功的最长时间。如果 timeout 被破坏，将引发 AirflowSensorTimeout 异常并且传感器立即失效而不重试。

## 服务水平协议
SLA 或服务级别协议是对任务应该花费的最长时间的期望。SLA 上的任务不会被取消 - 他们可以运行到完成。要为任务设置 SLA，请将 datetime.timedelta 对象传递给 任务/操作员 的 sla 参数。如果您想运行自己的逻辑，您还可以提供一个 sla_miss_callback 将在错过 SLA 时调用的对象。

## 特别例外
如果您想自己控制任务的状态，Airflow 提供了两个可以引发的特殊异常：
* AirflowSkipException 将当前任务标记为已跳过
* AirflowFailException 将当前任务标记为失败，忽略任何剩余的重试尝试

## 僵尸/亡灵任务
僵尸任务是应该运行但突然死亡的任务。不死任务是不应该运行但正在运行的任务。

## 执行器配置
一些执行器允许可选的任务配置。这是通过 Task 或 Operator 的 executor_config 参数实现的。
