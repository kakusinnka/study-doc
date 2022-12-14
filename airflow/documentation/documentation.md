# Documentation  [Apache Airflow](https://airflow.apache.org/docs/)
Apache Airflow Core，包括 Web 服务器、调度程序、CLI 和其他最小化 Airflow 安装所需的组件。  
Version: 2.2.5

## Home
* Airflow 是一个以编程方式创作、安排和监控工作流程的平台。
* 使用 Airflow 将工作流创作为任务的有向无环图 (DAG)。
* Airflow 不是数据流解决方案。任务不会将数据从一个移动到另一个。

## Quick Start
* Running Airflow locally -> quick_start\Running_Airflow_Locally.md  
  成功安装需要 Python 3 环境。  
  目前官方只支持 pip 安装。
* Running Airflow in Docker -> quick_start\Running_Airflow_in_Docker.md

## Installation
* 介绍了您在考虑如何安装 Airflow 时可能使用的安装选项。Airflow 由许多组件组成，通常分布在许多物理机或虚拟机中，因此 Airflow 的安装可能非常复杂，具体取决于您选择的选项。
* 1，先决条件。2，依赖项。 -> installation\Dependencies.md。3，Installation -> installation\Installation.md

## Tutorials
* 1，基础概念 -> tutorials\Example_Pipeline_definition.md
* 2，构建运行管道 -> tutorials\Building_Running_Pipeline.md

## Tutorial on the TaskFlow API
本教程以常规 Airflow 教程为基础，特别关注使用作为 Airflow 2.0 的一部分引入的 TaskFlow API 范例编写数据管道，并将其与使用传统范例编写的 DAG 进行对比。此处选择的数据管道是一个简单的 ETL 模式，具有提取、转换和加载三个单独的任务。 -> Tutorial_on_the_TaskFlow_API.
* 示例“TaskFlow API”ETL 管道
* 这是一个 DAG 定义文件
* 实例化一个 DAG
* 任务
* DAG的主要流程
* 和 1.0 进行对比
* 在 Docker 或虚拟环境中使用 TaskFlow API
* 多输出推理
* 在装饰任务和传统任务之间添加依赖关系
* 在装饰任务和传统任务之间使用 XCom
* 在装饰任务中访问上下文变量
* 在装饰任务中访问上下文变量

## How-to Guides
这些操作指南将引导您完成使用和配置 Airflow 环境的常见任务。

## UI / Screenshots
Airflow UI 可让您轻松监控数据管道并对其进行故障排除。 -> UI_Screenshots.md

## Concepts
在这里，您可以找到有关 Airflow 的每个核心概念及其使用方法的详细文档，以及高级架构概述。 -> Concepts

## Executor
Concepts/Concepts.md#Executor

## DAG Runs
DAGRuns.md

## Plugins
Plugins.md

## Security
Security.md

## Logging & Monitoring
LoggingMonitoring.md

## Time Zoes
Time_Zones.md

## Using the CLI
### 设置 Bash/Zsh 完成
## 创建连接
### 将 DAG 结构导出为图像
### 显示 DAG 结构
### 格式化命令输出

## 一体化(Integration)
Airflow 有一种机制，允许您扩展其功能并与其他系统集成。

## Kubernetes
Apache Airflow 旨在成为一个对 Kubernetes 非常友好的项目，许多用户在 Kubernetes 集群中运行 Airflow，以便利用 Kubernetes 提供的更高的稳定性和自动缩放选项。
### Kubernetes 的 Helm Chart
我们为 Airflow 维护官方 Helm chart，帮助您定义、安装和升级部署。Helm Chart 使用由社区维护和发布的官方 Docker 镜像和 Dockerfile
### Kubernetes 执行器
Kubernetes Executor 允许您将所有 Airflow 任务作为单独的 Pod 在 Kubernetes 上运行.
### KubernetesPodOperator
KubernetesPodOperator 允许您在 Kubernetes 上创建 Pod。
### Pod 突变钩子
Airflow 本地设置文件 (airflow_local_settings.py) 可以定义一个 pod_mutation_hook 函数，该函数能够在将 pod 对象发送到 Kubernetes 客户端进行调度之前对其进行突变。

## Lineage
不知道在说啥。

## DAG序列化
通过DAG 序列化，我们的目标是将 Web 服务器与 DAG 解析分离，这将使 Web 服务器非常轻量级。
![DAG序列化](../image/dag_serialization.png)
### Dag 序列化设置
```
[core]
min_serialized_dag_update_interval = 30
min_serialized_dag_fetch_interval = 10
max_num_rendered_ti_fields_per_task = 30
```
* min_serialized_dag_update_interval：此标志设置最小间隔（以秒为单位），在此之后应更新数据库中的序列化 DAG。
* min_serialized_dag_fetch_interval：此选项控制当序列化 DAG 已加载到 Web 服务器的 DagBag 中时，从数据库中重新获取序列化 DAG 的频率。
* max_num_rendered_ti_fields_per_task：此选项控制每个任务存储在数据库中的最大渲染任务实例字段数。
### 限制
### 使用不同的 JSON 库
要使用不同的 JSON 库而不是标准 json 库，您需要在本地 Airflow 设置文件 ( airflow_local_settings.py) 中定义一个变量，如下所示：
```
import ujson

json = ujson
```

## Modules Management
ModulesManagement.md


## Airflow的发布流程和版本政策
### 弃用政策
### 实验功能

## 变更日志

## 最佳实践
BestPractices.md

## 生产部署
ProductionDeployment.md

## 常问问题
FAQ.md