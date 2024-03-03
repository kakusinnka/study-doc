# Docker 简介
Docker 是一个用于开发、发布和运行应用程序的开放平台。借助 Docker，您可以将应用程序与基础架构分开，并将基础架构视为托管应用程序。Docker 可帮助您更快地交付代码、更快地测试、更快地部署，并缩短编写代码和运行代码之间的周期。

在本实验中，您将学习如何：
* 生成、运行和调试 Docker 容器。
* 从 Docker Hub 和 Google Artifact Registry 拉取 Docker 映像。
* 将 Docker 映像推送到 Google Artifact Registry。

## 将映像推送到由 Artifact Registry 托管
若要将映像推送到由 Artifact Registry 托管的专用注册表，需要使用注册表名称标记映像。格式为 <regional-repository>-docker.pkg.dev/my-project/my-repo/my-image 。

您必须先创建存储库，然后才能将任何映像推送到该存储库。推送映像无法触发存储库的创建。

# [Kubernetes Engine: Qwik Start (GSP100)](../labs/GSP100.md)
Google Kubernetes Engine (GKE) 提供了一个托管式环境，您可以使用 Google 基础设施在其中部署、管理和扩缩容器化应用。Kubernetes Engine 环境由多个机器（具体来讲，就是 Compute Engine 实例）组成，这些机器组合在一起形成容器集群。

# [使用 Kubernetes 编排云](../labs/GSP021.md)

# [在 Google Cloud 中部署到 Kubernetes](../labs/GSP318.md)