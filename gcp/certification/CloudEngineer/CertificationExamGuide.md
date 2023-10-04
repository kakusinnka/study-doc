# 认证考试指南
助理云工程师负责部署和保护应用程序和基础设施、监控多个项目的运营并维护企业解决方案以确保它们满足目标性能指标。  
此人拥有使用公共云和本地解决方案的经验。他们能够使用 Google Cloud 控制台和命令行界面执行基于平台的常见任务，以维护和扩展一个或多个部署的解决方案，这些解决方案利用 Google Cloud 上 Google 管理或自我管理的服务。

## 第 1 部分：设置云解决方案环境
### 1.1 设置云项目和帐户。活动包括：
* 创建资源层次结构
* 将组织策略应用于资源层次结构
* 授予成员项目中的 IAM 角色
* 管理 Cloud Identity 中的用户和群组（手动和自动）
* 在项目中启用 API
* 在 Google Cloud 运维套件中配置和设置产品

### 1.2 管理计费配置。活动包括：
* 创建一个或多个结算帐户
* 将项目链接到结算帐户
* 建立计费预算和提醒
* 设置帐单导出

### 1.3 安装和配置命令行界面 (CLI)，特别是 Cloud SDK（例如，设置默认项目）。

## 第 2 部分：规划和配置云解决方案
### 2.1 使用定价计算器规划和估算 Google Cloud 产品使用情况

### 2.2 规划和配置计算资源。考虑因素包括：
* 为给定工作负载选择适当的计算选项（例如，Compute Engine、Google Kubernetes Engine、Cloud Run、Cloud Functions）
* 根据情况使用可抢占式虚拟机和自定义机器类型

### 2.3 规划和配置数据存储选项。考虑因素包括：
* 产品选择（例如 Cloud SQL、BigQuery、Firestore、Cloud Spanner、Cloud Bigtable）
* 选择存储选项（例如区域永久性磁盘、区域平衡永久性磁盘、标准、近线、冷线、存档）

### 2.4 规划和配置网络资源。任务包括：
* 差异化的负载平衡选项
* 识别网络中的资源位置以确保可用性
* 配置云端 DNS

## 第 3 部分：部署和实施云解决方案
### 3.1 部署和实施 Compute Engine 资源。任务包括：
* 使用 Google Cloud 控制台和 Cloud SDK (gcloud) 启动计算实例（例如，分配磁盘、可用性政策、SSH 密钥）
* 使用实例模板创建自动扩缩的托管实例组
* 为实例生成/上传自定义 SSH 密钥
* 安装和配置 Cloud Monitoring and Logging Agent
* 评估计算配额并请求增加

### 3.2 部署和实施 Google Kubernetes Engine 资源。任务包括：
* 安装和配置 Kubernetes (kubectl) 的命令行界面 (CLI)
* 部署具有不同配置的 Google Kubernetes Engine 集群，包括 AutoPilot、区域集群、私有集群等。
* 将容器化应用程序部署到 Google Kubernetes Engine
*  配置 Google Kubernetes Engine 监控和日志记录

### 3.3 部署和实施 Cloud Run 和 Cloud Functions 资源。任务包括（如适用）：
* 部署应用程序并更新扩展配置、版本和流量分配
* 部署接收 Google Cloud 事件（例如，Pub/Sub 事件、Cloud Storage 对象更改通知事件）的应用程序

### 3.4 部署和实施数据解决方案。任务包括：
* 使用产品初始化数据系统（例如 Cloud SQL、Firestore、BigQuery、Cloud Spanner、Pub/Sub、Cloud Bigtable、Dataproc、Dataflow、Cloud Storage）
* 加载数据（例如，命令行上传、API 传输、导入/导出、从 Cloud Storage 加载数据、将数据流式传输到 Pub/Sub）

### 3.5 部署和实施网络资源。任务包括：
* 创建带有子网的 VPC（例如自定义模式 VPC、共享 VPC）
* 使用自定义网络配置（例如，仅限内部的 IP 地址、Google 私有访问、静态外部和私有 IP 地址、网络标签）启动 Compute Engine 实例
* 为 VPC 创建入口和出口防火墙规则（例如，IP 子网、网络标签、服务帐户）
* 使用 Cloud VPN 在 Google VPC 和外部网络之间创建 VPN
* 创建负载均衡器以将应用程序网络流量分配到应用程序（例如，全局 HTTP(S) 负载均衡器、全局 SSL 代理负载均衡器、全局 TCP 代理负载均衡器、区域网络负载均衡器、区域内部负载均衡器）

### 3.6 使用 Cloud Marketplace 部署解决方案。任务包括：
* 浏览 Cloud Marketplace 目录并查看解决方案详细信息
* 部署 Cloud Marketplace 解决方案

### 3.7 通过基础设施即代码实现资源。任务包括：
* 通过 Cloud Foundation Toolkit 模板构建基础设施并实施最佳实践
* 在 Google Kubernetes Engine 中安装和配置 Config Connector 以创建、更新、删除和保护资源

## 第 4 部分：确保云解决方案的成功运行
### 4.1 管理 Compute Engine 资源。任务包括：
* 管理单个虚拟机实例（例如启动、停止、编辑配置或删除实例）
* 远程连接到实例
* 将 GPU 连接到新实例并安装必要的依赖项
* 查看当前正在运行的虚拟机清单（实例 ID、详细信息）
* 使用快照（例如，从虚拟机创建快照、查看快照、删除快照）
* 使用映像（例如，从虚拟机或快照创建映像、查看映像、删除映像）
* 使用实例组（例如，设置自动扩展参数、分配实例模板、创建实例模板、删除实例组）
* 使用管理界面（例如 Google Cloud 控制台、Cloud Shell、Cloud SDK）

### 4.2 管理 Google Kubernetes Engine 资源。任务包括：
* 查看当前正在运行的集群清单（节点、Pod、服务）
* 浏览 Docker 镜像并在 Artifact Registry 中查看其详细信息
* 使用节点池（例如，添加、编辑或删除节点池）
* 使用广告连播（例如，添加、编辑或删除广告连播）
* 使用服务（例如添加、编辑或删除服务）
* 使用有状态应用程序（例如持久卷、有状态集）
* 管理水平和垂直自动缩放配置
* 使用管理界面（例如 Google Cloud 控制台、Cloud Shell、Cloud SDK、kubectl）

### 4.3 管理 Cloud Run 资源。任务包括：
* 调整应用程序流量分配参数
* 设置自动伸缩实例的伸缩参数
* 确定是运行 Cloud Run（完全托管）还是 Cloud Run for Anthos

### 4.4 管理存储和数据库解决方案。任务包括：
* 管理和保护 Cloud Storage 存储分区内和之间的对象
* 设置 Cloud Storage 存储桶的对象生命周期管理政策
* 执行查询以从数据实例检索数据（例如 Cloud SQL、BigQuery、Cloud Spanner、Datastore、Cloud Bigtable）
* 估算数据存储资源的成本
* 备份和恢复数据库实例（例如 Cloud SQL、Datastore）
* 在 Dataproc、Dataflow 或 BigQuery 中查看作业状态

### 4.5 管理网络资源。任务包括：
* 将子网添加到现有 VPC
* 扩展子网以拥有更多 IP 地址
* 保留静态外部或内部 IP 地址
* 使用 CloudDNS、CloudNAT、负载均衡器和防火墙规则

### 4.6 监控和记录。任务包括：
* 基于资源指标创建 Cloud Monitoring 警报
* 创建和提取 Cloud Monitoring 自定义指标（例如，来自应用程序或日志）
* 配置日志接收器以将日志导出到外部系统（例如本地系统或 BigQuery）
* 配置日志路由器
* 在 Cloud Logging 中查看和过滤日志
* 在 Cloud Logging 中查看特定日志消息详细信息
* 使用云诊断来研究应用程序问题（例如，查看 Cloud Trace 数据、使用 Cloud Debug 查看应用程序时间点）
* 查看 Google Cloud 状态

## 第 5 部分：配置访问和安全性
### 5.1 管理身份和访问管理 (IAM)。任务包括：
* 查看 IAM 政策
* 创建 IAM 政策
* 管理各种角色类型并定义自定义 IAM 角色（例如原始角色、预定义角色和自定义角色）

### 5.2 管理服务帐户。任务包括：
* 创建服务帐户
* 在 IAM 策略中使用具有最低权限的服务账户
* 将服务帐户分配给资源
* 管理服务账户的 IAM
* 管理服务帐户模拟
* 创建和管理短期服务帐户凭据

### 5.3 查看审计日志