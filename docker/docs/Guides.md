# Docker overview
Docker 是一个用于开发、运输和运行应用程序的开放平台。Docker 使您能够将应用程序与基础架构分开，以便您可以快速交付软件。使用 Docker，您可以像管理应用程序一样管理基础架构。通过利用 Docker 的方法来快速传输、测试和部署代码，您可以显着减少编写代码和在生产环境中运行代码之间的延迟。
## The Docker platform
Docker 提供了在称为容器的松散隔离环境中打包和运行应用程序的能力。
## What can I use Docker for?
* 快速、一致地交付您的应用程序
* 响应式部署和扩展
* 在相同的硬件上运行更多的工作负载
## Docker 架构
Docker 使用客户端-服务器架构。Docker客户端与 Docker守护进程对话，后者负责构建、运行和分发 Docker 容器的繁重工作。
![构架图](../images/architecture.svg)
* Docker 守护进程: Docker 守护进程 ( dockerd) 侦听 Docker API 请求并管理 Docker 对象，例如图像、容器、网络和卷。守护进程还可以与其他守护进程通信以管理 Docker 服务。
* Docker 客户端: Docker 客户端 ( docker) 是许多 Docker 用户与 Docker 交互的主要方式。
* Docker 桌面: Docker Desktop 是一个易于安装的应用程序，使您能够构建和共享容器化应用程序和微服务。Docker Desktop 包括 Docker 守护程序 ( dockerd)、Docker 客户端 ( docker)、Docker Compose、Docker Content Trust、Kubernetes 和 Credential Helper。
* Docker registries: Docker Registry 存储 Docker 映像。Docker Hub 是一个任何人都可以使用的公共 Registry，Docker 默认配置为在 Docker Hub 上查找镜像。您甚至可以运行自己的私有 Registry。当您使用docker pull或docker run命令时，所需的镜像将从您配置的 Registry 中提取。当您使用该docker push命令时，您的镜像将被推送到您配置的 Registry。
* Docker 对象: 当您使用 Docker 时，您正在创建和使用镜像、容器、网络、卷、插件和其他对象。镜像: 是一个只读模板，其中包含创建 Docker 容器的说明。通常，一个图像基于另一个图像，带有一些额外的定制。您可以创建自己的镜像，也可以只使用其他人创建并在 Registry 中发布的图像。要构建您自己的镜像，您可以使用简单的语法创建一个 Dockerfile ，用于定义创建和运行镜像所需的步骤。Dockerfile 中的每条指令都会在镜像中创建一个层。当您更改 Dockerfile 并重建镜像时，只会重建那些已更改的层。与其他虚拟化技术相比，这是使镜像如此轻巧、小巧和快速的部分原因。
* 容器: 容器是图像的可运行实例。您可以使用 Docker API 或 CLI 创建、启动、停止、移动或删除容器。您可以将一个容器连接到一个或多个网络，将存储附加到它，甚至可以根据其当前状态创建一个新图像。
* 底层技术: Docker 是用Go 编程语言编写的，并利用 Linux 内核的几个特性来提供其功能。Docker 使用一种称为容器 namespaces 的技术来提供隔离的工作空间。当您运行容器时，Docker 会为该容器创建一组 namespaces。这些命名空间提供了一层隔离。容器的每个方面都在单独的命名空间中运行，并且其访问仅限于该命名空间。

# Get Docker
您可以在多个平台上下载和安装 Docker。

# Get started
## 第 1 部分：概述
本指南包含有关如何开始使用 Docker 的分步说明。您将在本指南中学到和做的一些事情是：
* 构建并运行镜像作为容器
* 使用 Docker Hub 共享镜像
* 使用带有数据库的多个容器部署 Docker 应用程序
* 使用 Docker Compose 运行应用程序

## 第 2 部分：容器化应用程序
* 用 git 获取应用程序
* 写一个 Dockerfile, 使用 docker build 构建镜像。
* 使用 docker run 启动容器。

## 第 3 部分：更新应用程序
* 更新代码，重新 build 镜像，停止旧的容器，启动新容器（避免端口冲突）。

## 第 4 部分：共享应用程序
* 创建 Docker Hub
* 使用 docker push 推镜像（注意镜像名前半部分要与远程库匹配）。
* 使用 ddocker run 运行新做的镜像。

## 第 5 部分：保留数据库
一个容器中创建的文件在另一个容器中不可用。卷提供了将容器的特定文件系统路径连接回主机的能力。
* 使用docker volume create命令创建卷（在 Docker Desktop 中运行时，Docker 命令实际上是在您机器上的小型 VM 中运行。如果您想查看挂载点目录的实际内容，则需要查看该 VM 的内部）。
  ```
  docker run -dp 3000:3000 --mount type=volume,src=todo-db,target=/etc/todos getting-started
  ```
* 运行容器时，添加 --mount 指定卷装载的选项。
* 使用 docker volume inspect 命令查看卷的信息。Mountpoint是磁盘上存储数据的实际位置。

## 第 6 部分：使用绑定安装
绑定挂载是另一种类型的挂载，它允许您将主机文件系统中的目录共享到容器中。
```
docker run -it --mount type=bind,src="$(pwd)",target=/src ubuntu bash
```

## 第 7 部分：多容器应用程序
每个容器都应该做一件事，并且把它做好。
* 创建网络。
## 第 8 部分：使用 Docker Compose
## 第 9 部分：形象构建最佳实践
## 第 10 部分：下一步是什么？
# Language-specific guides
# Develop with Docker
# Deploy your app to the cloud
# Run your app in production
# Educational resources