# Google Kubernetes Engine 入门
欢迎来到 Google Kubernetes Engine 入门课程。 如果您对 Kubernetes（位于应用程序和硬件基础设施之间的软件层）感兴趣，那么您来对地方了！ Google Kubernetes Engine 为您提供 Kubernetes 作为 Google Cloud 上的托管服务。

本课程的目标是介绍 Google Kubernetes Engine（通常称为 GKE）的基础知识，以及如何将应用程序容器化并在 Google Cloud 中运行。 本课程首先对 Google Cloud 进行基本介绍，然后概述容器和 Kubernetes、Kubernetes 架构和 Kubernetes 操作。

# 课程信息
## 目标
* 讨论 Google Cloud 计算平台之间的差异。
* 讨论 Kubernetes 的组件和架构。
* 了解 Google 如何管理 Kubernetes 编排。
* 使用 Google Cloud 控制台和 gcloud/kubectl 命令创建和管理 Google Kubernetes Engine 集群。

# 课程介绍
课程简介解释了课程目标并预览了每个部分。

## 欢迎和入门指南
什么是 Kubernetes？  
Kubernetes 是一个软件容器的编排框架。 容器是一种比虚拟机更高效的打包和运行代码的方式。 Kubernetes 提供了在生产环境中大规模运行容器化应用程序所需的工具。

什么是谷歌 Kubernetes 引擎？  
Google Kubernetes Engine (GKE) 是 Kubernetes 的托管服务。

## 课程介绍
本课程的目标是介绍通常所说的 GKE 基础知识，以及如何将应用程序容器化并在 Google Cloud 中运行。  
介绍 Google Cloud，然后概述容器和 Kubernetes、Kubernetes 架构和 Kubernetes 操作。

# 谷歌云介绍
本课程的第一部分介绍云计算概念。 学习者将探索基本术语、Google Cloud 网络、Google Cloud 资源如何按层次结构进行管理以及可用于连接到 Google Cloud 以分配、更改和释放资源的工具。

## 介绍
在本课程的第一部分中，您将探索：云计算的定义。
* Google Cloud 为架构师和开发人员提供构建解决方案的服务。
* Google 强大的全球网络如何为 Google Cloud 服务提供支持。
* Google Cloud 资源的结构和管理方式。
* 确保您的组织不会意外面临巨额 Google Cloud 账单的工具。
* 以及与 Google Cloud 交互的四种不同方式来开始工作。

## 云计算和谷歌云
云计算是一种使用信息技术（IT）的方式，它具有这五个同样重要的特征。
* 首先，客户获得按需和自助服务的计算资源。通过 Web 界面，用户无需人工干预即可获得所需的处理能力、存储和网络。
* 其次，客户可以从任何有连接的地方通过互联网访问这些资源。
* 第三，云提供商拥有大量这些资源，并将它们分配给该池中的用户。这使得提供商可以批量购买并将节省的费用转嫁给客户。客户不必知道或关心这些资源的确切物理位置。
* 第四，资源具有弹性——这意味着它们是灵活的，如果他们需要更多资源，他们可以更快地获得更多资源。如果他们需要更少，他们可以缩减规模。
* 最后，客户只需按使用量付费，或按使用量预订。如果他们停止使用资源，他们就会停止付费。

## Google Cloud 计算产品
### Compute Engine
Compute Engine 是一种 IaaS 产品或基础设施即服务，它提供与物理数据中心类似的虚拟计算、存储和网络。  
Compute Engine 提供对预定义和自定义虚拟机配置的访问。

### GKE
GKE 在云环境中运行容器化应用程序，容器代表与其所有依赖项一起打包的代码。

### App Engine
App Engine 是一种完全托管的 PaaS 产品或平台即服务。PaaS 产品将代码绑定到库，提供对基础设施应用程序需求的访问。

### Cloud Functions
Cloud Functions 是一种轻量级、基于事件的异步计算解决方案，用于创建响应云事件的小型单一用途函数，而无需管理服务器或运行时环境。云函数通常称为函数即服务。

### Cloud Run
Cloud Run 是一个托管计算平台，可通过 Web 请求或 Pub/Sub 事件运行无状态容器。它基于 Knative 构建，Knative 是一个基于 Kubernetes 构建的开放 API 和运行时环境，可让您自由地在不同环境和平台之间移动工作负载。

## 谷歌网络
* 谷歌网络通过使用全球 100 多个内容缓存节点，为客户的应用程序提供尽可能高的吞吐量和尽可能低的延迟。
* 多个服务位置来提高可用性、耐用性和延迟等质量。每个位置都分为几个不同的区域和单区域。区域代表独立的地理区域，由单区域组成。单区域是部署 Google Cloud 资源的区域。您还可以在不同区域运行资源。这对于拉近应用程序与世界各地用户的距离非常有用，并且还可以在整个单区域发生问题（例如自然灾害）时提供保护。

## 资源管理
您使用的每个 Google Cloud 资源都必须属于一个项目。项目是所有 Google Cloud 资源的容器。它提供了一种组织资源、管理计费和控制访问的方法。

Google Cloud 的资源层次结构包含四个级别，从下往上依次为：资源、项目、文件夹和组织节点。  
资源处于第一级。它们代表容器、虚拟机、BigQuery 中的表或 Google Cloud 中的任何其他内容。  
资源被组织成位于第二层的项目。  
项目可以组织到文件夹甚至子文件夹中。这些位于第三层。  
然后顶层是组织节点，其中包含组织中的所有项目、文件夹和资源。  

可以在项目、文件夹和组织节点级别定义策略。某些 Google Cloud 服务也允许将策略应用于单个资源。政策是向下继承的。

项目是启用和使用 Google Cloud 服务的基础，例如管理 API、启用计费、添加和删除协作者以及启用其他 Google 服务。  
每个项目都是组织节点下的一个独立实体，每个资源都属于一个项目。  
项目可以有不同的所有者和用户，因为它们是单独计费和管理的。  
每个 Google Cloud 项目都具有三个标识属性：项目 ID、项目名称和项目编号。  
项目ID是Google分配的全球唯一标识符，创建后无法更改。它们就是我们所说的不可变的。项目 ID 在不同的上下文中使用，以告知 Google Cloud 要使用的确切项目。  
项目名称是用户创建的。它们不必是唯一的，并且可以随时更改，因此它们不是一成不变的。  
Google Cloud 还为每个项目分配一个唯一的项目编号。它们主要由 Google Cloud 在内部使用来跟踪资源。

您可以使用文件夹将项目按层次结构分组到组织下。文件夹允许您按部门对这些资源进行分组。

借助 IAM，管理员可以应用策略来定义谁可以执行什么操作以及对哪些资源执行操作。  
IAM 政策的“谁”部分可以是 Google 帐号、Google 群组、服务帐号或 Cloud Identity 域名。  
IAM 策略的“可以做什么”部分由角色定义。IAM 角色是权限的集合。当您将角色授予主体时，您将授予该角色包含的所有权限。

当您将角色授予主体时，您将授予该角色包含的所有权限。

## 结算
结算是在 Google Cloud 资源层次结构的项目级别建立的。  
一个结算帐号可以关联到零个或多个项目，但未关联到结算帐号的项目只能使用免费的 Google Cloud 服务。  
计费子账户可用于按项目单独计费。一些转售 Google Cloud 服务的 Google Cloud 客户为其自己的每个客户使用子帐号。

* 您可以在计费帐户级别或项目级别定义预算。
* 要在成本接近您的预算限额时收到通知，您可以创建警报。
* 报告是 Google Cloud 控制台中的一个可视化工具，可让您根据项目或服务监控支出。
* Google Cloud 还实现了配额，旨在防止由于错误或恶意攻击而过度消耗资源。

配额有两种类型：费率配额和分配配额。费率配额会在特定时间后重置。分配配额控制您的项目中可以拥有的资源数量。

## 与 Google Cloud 交互
您可以使用四种 Google 产品来访问 Google Cloud 并与之交互。Google Cloud 控制台、Cloud SDK 和 Cloud Shell、API 以及 Google Cloud 应用。  
* 首先是Google Cloud Console，这是Google Cloud的图形用户界面或 GUI，它可以帮助您在一个简单的基于 Web 的界面中部署、扩展和诊断生产问题。
* 第二个产品是 Cloud SDK 和 Cloud Shell。
  * Cloud SDK 是一组可用于管理 Google Cloud 上托管的资源和应用的工具。
  * Cloud Shell 提供直接从浏览器对云资源的命令行访问。
* 访问 Google Cloud 的第三种方式是通过应用程序编程接口 (API)。Cloud Console 包含一个名为 Google API Explorer 的工具，该工具显示哪些 API 可用以及哪些版本可用。
* 最后，访问 Google Cloud 并与之交互的第四种方式是使用 Google Cloud 应用程序，该应用程序可以用于启动、停止和使用 SSH 连接到 Compute Engine 实例并查看每个实例的日志。它还允许您停止和启动 Cloud SQL 实例。此外，您还可以通过查看错误、回滚部署和更改流量分配来管理 App Engine 上部署的应用程序。

## 实验简介：访问 Google Cloud 控制台和 Cloud Shell
从 Google Cloud 控制台和 Cloud Shell 创建存储桶、虚拟机和服务帐号。您还可以练习通过 Cloud Shell 执行其他命令。

## GCP 和 Qwiklabs 入门
略

## 访问 Google Cloud 控制台和 Cloud Shell
### 概览
略

### 目标
略

### 实验设置
略

### 任务 1. 探索 Google Cloud 控制台
略

### 任务 2. 了解 Cloud Shell
略

### 任务 3. 在 Cloud Shell 中使用 Cloud Storage
略

### 任务 4. 探索 Cloud Shell 代码编辑器
略

# 容器和 Kubernetes 简介
本课程的第二部分研究软件容器及其为应用程序部署带来的好处。 学习者探索容器和容器映像、Cloud Build、Kubernetes 和 Google Kubernetes Engine。

## 介绍
略

## 容器
不久前，部署应用程序的常见方式是在本地计算机上。要设置一台，您需要物理空间、电力、冷却和网络连接。然后您需要安装操作系统、任何软件依赖项，最后是应用程序。当您需要更多处理能力、冗余、安全性或可扩展性时，您需要添加更多计算机。每台计算机都有一个单一用途是很常见的，例如数据库、Web 服务器或内容交付。这种做法浪费了资源，并且需要花费大量时间来部署、维护和扩展。

然后是虚拟化，这是创建物理资源（例如服务器、存储设备或网络）的虚拟版本的过程。虚拟化使得在一台本地计算机上运行多个虚拟服务器和操作系统成为可能。打破操作系统对底层硬件的依赖并允许多个虚拟机共享该硬件的软件层称为虚拟机管理程序。

您不必虚拟化整个机器，甚至整个操作系统，只需虚拟化用户空间即可。用户空间是驻留在内核之上的所有代码，它包括应用程序及其依赖项。这就是创建容器的意义。

## 容器镜像
应用程序及其依赖项称为映像，而容器只是映像的运行实例。通过将软件构建到容器映像中，开发人员可以打包和发布应用程序，而无需担心它将运行的系统。但要构建和运行容器映像，您需要软件。

容器具有隔离工作负载的能力，这种能力来自多种 Linux 技术的组合。
* 首先是Linux进程的基础。每个Linux进程都有自己的虚拟内存地址空间，与所有其他进程分开，并且Linux进程可以快速创建和销毁。
* 下一个技术是 Linux 命名空间。容器使用 Linux 命名空间来控制应用程序可以看到的内容，例如进程 ID 号、目录树、IP 地址等。
* 第三种技术是Linux cgroups。Linux cgroup 控制应用程序可以使用的内容，例如 CPU 时间、内存、I/O 带宽和其他资源的最大消耗。
* 最后，容器使用联合文件系统将所需的所有内容捆绑到一个整洁的包中。

容器镜像是分层结构的，用于构建镜像的工具从称为容器清单的文件中读取指令。每个层都是只读的，但是当容器从该映像运行时，它还将有一个可写的、临时的最顶层。当您编写 Dockerfile 时，应从最不可能更改的层开始，将最可能更改的层放在底部。

当从镜像启动新容器时，容器运行时会在底层之上添加一个新的可写层。该层称为容器层。对正在运行的容器所做的所有更改，例如写入新文件、修改现有文件和删除文件，都会写入这个薄的可写容器层。它们是短暂的，这意味着当删除容器时，该可写层的内容将永远丢失。多个容器可以共享对同一底层映像的访问，同时仍然维护自己的数据状态。

Google 提供了一项用于构建容器的托管服务，称为 Cloud Build。配置构建步骤来获取依赖项、编译源代码、运行集成测试或使用 Docker、Gradle 和 Maven 等工具。Cloud Build 中的每个构建步骤都在 Docker 容器中运行。从那里，Cloud Build 可以将新构建的映像交付到各种执行环境，包括 Google Kubernetes Engine、App Engine 和 Cloud Functions。

## 实验室简介：使用 Cloud Build
您将使用提供的代码来构建 Docker 容器映像和 Dockerfile。您将容器上传到 Google Cloud ArtifactRegistry，这是一个私有 Docker 存储库，用于安全地存储和管理 Docker 映像。

## 实验：使用 Cloud Build
### 概览
在本实验中，您将使用 Cloud Build 基于提供的代码和 Dockerfile 构建一个 Docker 容器映像。然后将容器上传到 Container Registry。

### 目标
在本实验中，您将学习如何执行以下任务：
* 使用 Cloud Build 构建和推送容器
* 使用 Container Registry 存储和部署容器

### 实验设置
略

### 任务 1. 确认已启用所需的 API
略

### 任务 2. 使用 DockerFile 和 Cloud Build 构建容器
略

### 任务 3：使用 build 配置文件和 Cloud Build 构建容器
略

### 任务 4：使用 build 配置文件和 Cloud Build 构建并测试容器
略

## Kubernetes
Kubernetes 是一个用于管理容器化工作负载和服务的开源平台。它可以轻松地在许多主机上编排许多容器，将它们扩展为微服务，并轻松部署部署和回滚。在最高级别上，Kubernetes 是一组 API，可用于在一组称为集群的节点上部署容器。该系统分为一组作为控制平面运行的主要组件和一组运行容器的节点。在 Kubernetes 中，节点代表一个计算实例，就像一台机器。Kubernetes 支持声明式配置。Kubernetes 还允许命令式配置。

Kubernetes 支持不同的工作负载类型。它支持无状态应用程序，例如 Nginx 或 Apache Web 服务器，以及可以持久存储用户和会话数据的有状态应用程序。它还支持批处理作业和守护程序任务。Kubernetes 可以根据资源利用率自动扩展和扩展容器化应用程序。Kubernetes 允许用户指定工作负载的资源请求级别和资源限制。

## Google Kubernetes Engine
GKE 旨在帮助部署、管理和扩展容器化应用程序的 Kubernetes 环境。GKE 是完全托管的，这意味着无需配置底层资源，并且使用容器优化的操作系统来运行工作负载。GKE 自动升级功能可确保集群始终升级到最新稳定版本的 Kubernetes。

# GKE 架构
本课程的第三部分探讨 Kubernetes 集群的组件以及它们如何协同工作。 学习者使用 Google Kubernetes Engine 部署 Kubernetes 集群，将 Pod 部署到 GKE 集群，并查看和管理不同的 Kubernetes 对象。

## 介绍