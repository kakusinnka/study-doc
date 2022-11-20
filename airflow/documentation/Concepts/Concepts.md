# 架构 ArchitectureOverview.md
## 架构概述
* 工作负载
* 控制流
* 用户界面

# 工作负载 dag.md
## DAGs
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

## 任务
* 关系
* 任务实例
* 超时
* 服务水平协议
* 特别例外
* 僵尸/亡灵任务
* 执行器配置

## Operators(操作员)
* Jinja 模板
* 保留参数关键字

## Sensors

## 可延迟的 Operators(操作员) 和 Triggers(触发器)
* 使用可延迟 Operators
* 编写可延迟的 Operators
* 高可用性
* 智能传感器

## 智能传感器
* 启用/禁用智能传感器
* 在智能传感器服务中支持新的 Operators
* 迁移到可延迟 Operators

## 任务流
* 历史

## Executor(执行者)
* Executor(执行者) 类型

## 调度器
* DAG 文件处理
* 使用未来日期触发 DAG
* 运行多个调度程序
* 微调您的调度程序性能

## Pools
* 使用多个池槽

## Timetables(时刻表)

## 优先权重

## 集群策略
* 例子
* 任务政策
* 任务实例突变

# 沟通
## Xcoms
* 自定义 XCom 后端
* 在容器中使用自定义 XCom 后端
* 通过 Helm 在 K8s 中使用自定义后端

## Variables(变量)

## 连接和挂钩
* 挂钩
* 自定义连接

## 参数
* 将参数添加到 DAG
* 在任务中引用参数
* 任务级参数
* JSON 模式验证
* 禁用运行时参数修改