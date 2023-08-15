# Google Cloud 基础知识：核心基础设施
Google Cloud 基础知识：核心基础设施介绍了使用 Google Cloud 的重要概念和术语。 本课程通过视频和动手实验，展示并比较了许多 Google Cloud 的计算和存储服务，以及重要的资源和策略管理工具。

# 课程信息
## 目标
* 确定 Google Cloud 产品和服务的目的和价值。
* 与 Google Cloud 服务交互。
* 选择并使用 Google Cloud 上的应用程序部署环境：App Engine、Google Kubernetes Engine 和 Compute Engine。
* 选择并使用 Google Cloud 的存储选项：Cloud Storage、Cloud SQL、Cloud Bigtable 和 Firestore。

# 课程介绍
本部分欢迎学员学习 Google Cloud 基础知识：核心基础设施课程，并概述课程结构和目标。

## 课程简介
Google Cloud 产品系列可以大致分为 计算、存储、大数据、机器学习和应用服务。  
实现五个关键学习目标：
* 认识到 Google Cloud 产品和服务的目的和价值。
* 选择和使用 Google Cloud 上的多种应用环境。
* 选择和使用 Google Cloud 存储方案。
* 与 Google Cloud 服务交互。
* 描述客户使用 Google Cloud 的各种方式。

# 谷歌云简介
本部分介绍了使用 Google Cloud 的一些主要优势。 在这里，我们介绍了 Google 网络基础设施的组件，并探讨了基础设施即服务 (IaaS) 和平台即服务 (PaaS) 之间的差异。

## 云计算概览
“云计算” 具有五个同等重要的特征：
* 客户可以获得按需、自助式的计算资源。
* 客户可以从可联网的任何位置，通过互联网访问这些资源。
* 云服务提供商拥有庞大的资源池，并将池中的资源分配给用户。
* 资源具有弹性，也就是说资源是灵活的。
* 客户只需为实际使用的资源付费。

回顾一下历史：
* 第一波浪潮称为主机托管，主机托管为用户提供了财务效率方面的优势，因为用户可以租用实体空间而不必投资数据中心不动产。
* 虚拟化数据中心是该趋势的第二波浪潮。
* Google改为采用一种基于容器的架构 一种全自动化、有弹性的第三波云架构。

## IaaS 和 PaaS
IaaS 产品提供原始计算、存储和网络功能、并通过虚拟方式将其组织为与实体数据中心相似的资源。  
PaaS 产品将代码与库绑定在一起，这些库支持访问应用所需的基础架构。  
在 IaaS 模式中，客户为提前分配好的资源付费。在 PaaS 模式中客户为其实际使用的资源付费。

## Google Cloud 网络
Google Cloud 在 Google 自己的全球网络上运行。该网络旨在通过利用全球 100 多个内容缓存节点，为客户的应用程序提供尽可能高的吞吐量和尽可能低的延迟。这些位置缓存了高需求内容以便更快地访问，从而允许应用程序响应来自提供最快响应时间的位置的用户请求。  

---

regions 代表独立的地理位置，由 zones 组成。  
zones 是部署 Google Cloud 资源的区域。  
![](../images/location-regions-zones.png)
![](../images/location-regions-zones-real.png)

## 对环境造成的影响
略

## 安全
* 硬件基础架构层安全包含三项关键安全特性：
  * 硬件设计和来源
  * 安全启动堆栈
  * 现场安全
* 服务部署层安全：服务间通信加密。
* 用户身份层安全：集中身份服务。
* 存储服务层安全：数据加密。
* 内部通信层安全：Google Front End，拒绝服务攻击(DoS)防护。
* Google的运维安全层的四项安全特性：
  * 入侵检测。
  * 降低内部人员攻击风险。
  * 员工 U2F 的使用。
  * 严格的软件开发实践。

## 开源生态系统
Google 利用开源许可公布了关键技术元素，以便打造丰富的生态系统，为客户提供除 Google 以外的更多选择。

## 价格和结算
在线价格计算器可帮你估算费用。  
我们提供的一些工具可以助你一臂之力：预算，提醒，报告，配额。

## 测验：Google Cloud 简介
略

# 云中的资源和访问
本节探讨如何通过项目组织资源，以及如何通过名为身份和访问管理 (IAM) 的工具与适当的员工共享对这些资源的访问权限。 也在本节中，我们确定了与 Google Cloud 交互的不同方式。

## Google Cloud 资源层次结构
Google Cloud 的资源层次结构包含四个级别自下而上分别是：资源，项目，文件夹以及一个组织节点。  
资源层次结构直接关系到你在使用 Google Cloud 时管理和应用政策的方式。定义政策时，可以在项目，文件夹以及组织节点级别进行，部分 Google Cloud 服务还允许 向单个资源应用政策。政策会向下继承，也就是说，如果向某个文件夹应用了政策，该政策也会应用于这个文件夹内的所有项目。  
![资源层次结构](../images/resource-level.png)
* 项目是启用和使用 Google Cloud 服务的基础，每个项目都是组织节点下的一个独立实体，每个资源都属于一个项目，项目可以有不同的所有者和用户，因为项目是分开结算和管理的。每个Google Cloud 项目具有三个标识特性：项目ID、项目名称以及项目编号。
* 利用文件夹你可以按照自己选择的粒度级别为资源指定政策。一个文件夹内的资源会继承分配给该文件夹的政策和权限，文件夹可以包含项目和或其他文件夹。使用文件夹可以以层次结构的形式整理组织名下的多个项目。
* 组织节点是 Google Cloud 层次结构中最高级别的资源，与帐号关联的其他所有资源都位于这个节点之下，包括文件夹，项目和其他资源。

## Identity and Access Management (IAM)
借助 IAM，管理员可以应用策略来定义谁可以执行什么操作以及对哪些资源执行操作。  
IAM 政策的“谁”部分可以是 Google 帐号、Google 群组、服务帐号或 Cloud Identity 域名。  
IAM 策略的“可以做什么”部分由角色定义。IAM 角色是权限的集合。当您将角色授予主体时，您将授予该角色包含的所有权限。  
![资源层次结构](../images/resource-level2.png)  
![角色和政策](../images/role-policy.png)  

---

IAM 中有三种角色：基本角色、预定义角色和自定义角色。  
![三种角色](../images/roles.png)

第一种角色类型是基本角色。基本角色的范围相当广泛。当应用于 Google Cloud 项目时，它们会影响该项目中的所有资源。  
基本角色包括所有者、编辑者、查看者和计费管理员。  
![基本角色](../images/basic-role.png)

第二种角色，即预定义角色。特定的 Google Cloud 服务提供了一组预定义的角色，甚至定义了可以应用这些角色的位置。任何拥有这些角色的人都可以执行一组特定的预定义操作。  
![预定义角色](../images/predefined-role.png)

许多公司使用“最小权限”模型，在该模型中，组织中的每个人都被授予完成其工作所需的最小权限。这就是您使用自定义角色的时候。  
![自定义角色](../images/custom-role.png)
在开始创建自定义角色之前，请注意两个重要细节：
* 首先，您需要管理定义您创建的自定义角色的权限。
* 其次，自定义角色只能应用于项目级别或组织级别。它们不能应用于文件夹级别。

## 服务帐号
您可以将服务帐号关联到某个 Compute Engine 实例，以便在该实例上运行的应用可以使用该服务帐号证明其身份。然后，您可以向服务帐号授予 IAM 角色，让该服务帐号（以及实例上的应用）可以访问相应的 Google Cloud 资源。

## Cloud Identity
统一的身份、访问权限、应用和端点管理 (IAM/EMM) 平台。  
借助名为 Cloud Identity 的工具，组织可以使用 Google 管理控制台定义政策并管理其用户和群组。  
管理员可以使用在现有 Active Directory 或 LDAP 系统中使用的用户名和密码登录和管理 Google Cloud 资源。  
使用 Cloud Identity 还意味着，当有人离开组织时，管理员可以使用 Google 管理控制台禁用其帐户并将其从群组中删除。  

## 与 Google Cloud 交互
有四种方式可以访问 Google Cloud 并与之交互。Cloud Console、Cloud SDK 和 Cloud Shell、API 以及 Cloud Console 移动应用。
* 首先是 Google Cloud Console，它是 Google Cloud 的图形用户界面 GUI，可帮助您在简单的基于 Web 的界面中部署、扩展和诊断生产问题。
* 其次是通过 Cloud SDK 和 Cloud Shell。Cloud SDK 是一组工具，可用于管理 Google Cloud 上托管的资源和应用。Cloud Shell 提供直接从浏览器对云资源的命令行访问。
* 访问 Google Cloud 的第三种方式是通过应用程序编程接口 (API)。以便您编写的代码可以控制它们。
* 最后，访问 Google Cloud 并与之交互的第四种方式是使用 Cloud Console 移动应用程序，该应用程序可用于执行一些简单的任务。

## Google Cloud 基础知识：Cloud Marketplace 使用入门
Google Cloud Marketplace 可让您快速部署在 Google Cloud 上运行的功能软件包。即使您不熟悉 Compute Engine 或 Cloud Storage 等服务，也可以启动一个熟悉的软件包，而无需手动配置软件、虚拟机 (VM) 实例、存储空间或网络设置。您可以立即部署软件包，稍后在应用需要额外容量时扩缩该部署。

### 概览
在本实验中，您将使用 Cloud Marketplace 轻松快速地在 Compute Engine 实例中部署 LAMP 技术栈。

### 目标
在此实验中，您将学习如何使用 Cloud Marketplace 启动一个解决方案。

### 任务 1. 登录 Google Cloud Platform (GCP) 控制台
略

### 任务 2. 使用 Cloud Marketplace 部署一个 LAMP 技术栈
略

### 任务 3. 验证您的部署
略

### 恭喜！
略

### 结束实验
略

### 其他资源
略

## 测验：Google Cloud 中的资源和访问
