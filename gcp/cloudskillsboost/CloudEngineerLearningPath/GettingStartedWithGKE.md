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
