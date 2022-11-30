# 架构 ArchitectureOverview.md
## 架构概述
* 工作负载
* 控制流
* 用户界面

# 工作负载
## DAGs dag.md
* 声明 DAG
* 加载 DAG
* 运行 DAG
* DAG 赋值
* 默认参数
* DAG 装饰器
* 控制流
* 动态 DAG
* DAG 可视化
* DAG 和 TASK 文档
* SubDAGs
* TaskGroups vs SubDAGs
* 打包 DAG
* .airflowignore
* DAG 依赖项

## 任务 task.md
* 关系
* 任务实例
* 超时
* 服务水平协议
* 特别例外
* 僵尸/亡灵任务
* 执行器配置

## Operators(操作员)
Operator 在概念上是预定义Task的模板，您可以在 DAG 中以声明方式定义它.

* Jinja 模板: Airflow 利用了 Jinja 模板的强大功能，这可以成为与宏结合使用的强大工具。
* 将字段呈现为 Python 对象: 可以 render_template_as_native_obj=True 传递给 DAG
* 保留参数关键字: 在 Apache Airflow 2.2.0 中，params 变量用于 DAG 序列化。

## Sensors
传感器是一种特殊类型的 Operator，旨在只做一件事：等待某事发生。它可以是基于时间的，或者等待一个文件，或者一个外部事件，但他所做的只是等待，直到有事情发生，然后成功，这样他们的下游任务才能运行。
* 与 Operators 非常相似，Airflow 有大量预建的传感器供您使用，既可以在核心 Airflow 中使用，也可以通过我们的供应商系统使用。

## 可延迟的 Operators(操作员) 和 Triggers(触发器)
Operators 和 Sensor 在整个运行期间占用一个完整的 worker slot(工作槽)，即使它们处于空闲状态。为了解决资源浪费，使用可延迟运算符，能够在知道必须等待时暂停自身并释放工作人员的能力，并将恢复它的工作交给称为Trigger。

* 使用可延迟 Operators: 使用可延迟运算符几乎是透明的.
* 编写可延迟的 Operators: 编写它们需要更多的工作。
* 高可用性
* 智能传感器

## 智能传感器
* 启用/禁用智能传感器
* 在智能传感器服务中支持新的 Operators
* 迁移到可延迟 Operators

## 任务流
使用纯 Python 代码而不是 Operators 编写大部分 DAG，那么 TaskFlow API 将使编写干净的 DAG 变得容易得多，而无需额外的样板，全部使用 @task 装饰器。

* 历史

## Executor(执行者)
执行器是任务实例运行的机制。它们有一个通用的 API 并且是“可插入的”，这意味着您可以根据您的安装需要更换执行器。Airflow 一次只能配置一个执行器；这是由配置文件[core]部分中的 executor 选项设置的。
* Executor(执行者) 类型

## 调度器 Scheduler.md
* DAG 文件处理
* 使用未来日期触发 DAG
* 运行多个调度程序
* 微调您的调度程序性能

## Pools 知识不足
Airflow pools 可用于限制任意任务集的执行并行性。

* 使用多个池槽

## Timetables(时刻表) 知识不足
DAG 的调度策略由 timetable “时间表” 决定。

## 优先权重 知识不足

## 集群策略 知识不足
* 例子
* 任务政策
* 任务实例突变

# 沟通
## Xcoms 知识不足
XComs（“交叉通信”的缩写）是一种让任务相互通信的机制，因为默认情况下任务是完全隔离的，并且可能在完全不同的机器上运行。

* 自定义 XCom 后端
* 在容器中使用自定义 XCom 后端
* 通过 Helm 在 K8s 中使用自定义后端

## Variables(变量)
变量是 Airflow 的运行时配置概念。一个全局的通用 键/值 存储，可以从您的任务中查询，并通过 Airflow 的用户界面轻松设置，或作为 JSON 文件批量上传。

## 连接和挂钩
Airflow 通常用于将数据拉取和推送到其他系统，因此它具有一流的连接概念，用于存储用于与外部系统对话的凭证。

* 挂钩：Hook 是外部平台的高级接口，可让您快速轻松地与他们交谈，而无需编写访问其 API 或使用特殊库的低级代码。它们通常也是构建 Operator 的基石。
* 自定义连接

## 参数
参数是 Airflow 为任务提供运行时配置的方式。

* 将参数添加到 DAG
* 在任务中引用参数
* 任务级参数：您还可以将 Params 添加到单个任务。
* JSON 模式验证
* 禁用运行时参数修改