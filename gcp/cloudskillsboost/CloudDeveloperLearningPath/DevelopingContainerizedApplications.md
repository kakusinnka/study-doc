# 课程介绍
* 定义容器和容器映像。
* 生成应用程序并将其打包到容器映像中。
* 确定用于创建、测试和保护容器的最佳做法。
* 了解 Cloud Run 和 Google Kubernetes Engine 的基础知识。

## 容器和镜像
### 什么是容器？
容器是以下组件的包：应用程序代码，依赖关系，编程语言运行时，软件库。

### 容器镜像
容器映像表示一个模板，该模板定义如何在运行时实现容器实例。容器映像将应用程序与应用程序运行所需的所有内容打包在一起。

### 以下是一些需要记住的事项
* 容器映像是包含文件的存档：它包括可执行文件、系统库、数据文件等。
* 容器映像是自包含的。应用程序需要运行的所有内容都在容器映像中。例如，如果应用程序是 Node.js 应用程序，则源文件与 Node.js 运行时一起位于映像中。
* 容器是容器映像的运行时实例，表示容器的运行进程。

### 运行容器
将应用程序打包到容器映像后，可以在任何位置运行它。在 Google Cloud 上，您可以在虚拟机的 Compute Engine 上运行容器，也可以在 Kubernetes 集群上运行容器，也可以在 Cloud Run 上运行容器。在本地计算机上，可以使用 Docker 或 Podman 容器运行时。

Docker 是一个开放平台，用于开发和运行基于容器的应用程序。

Podman 是一种开源 Linux 工具，用于使用基于开放容器计划 （OCI） 的容器构建和运行应用程序。

### 容器配置
![](../images/container-config.png)  
1. 容器映像包含应用程序以及应用程序运行所需的所有内容。
2. 最小容器映像只有一个程序文件和一个运行它的命令。
3. 某些编程语言需要运行时（Java，Python，Node.js）。
4. 应用程序可能需要其他系统依赖项才能工作。

## 使用 Docker 构建容器映像
![生成和打包应用程序](../images/container-build-package.png)  

![Docker and Buildpacks](../images/container-docker-buildpack.png)  
Docker 是一个开放平台，可用于在容器中打包和运行应用程序。它提供了用于管理容器生命周期（从开发和打包到部署）的工具。

Docker 允许您使用称为 Dockerfile 的脚本来表达应用程序构建过程。Dockerfile 提供了一种低级方法，以复杂性为代价提供了灵活性。

Dockerfile 是一个清单，详细说明了如何将源代码转换为容器镜像。

Buildpack 是构建容器映像的另一种方法。它们与 Docker 不同，它们提供了一种使用启发式方法生成和打包源代码来生成容器映像的便捷方法。

### 以下是关于 Dockerfile 指令的重要事项：
首先将容器映像放在舞台上，每个 Dockerfile 指令都会更改该暂存的容器映像。  
* FROM 指令下载要从中开始的基础映像。例如，基础映像可以是“golang”，并包含构建和运行软件所需的工具。
* COPY 指令从生成上下文（通常是包含 Dockerfile 的目录）中提取文件。
* RUN 指令允许您从容器映像运行程序，以更改映像中的文件。
* 其他指令会更改容器配置，该配置会指出要启动的程序文件以及如何启动。

## 使用 Buildpack 创建容器映像
![](../images/buildpack.png)  
Buildpack 是一种无需编写 Dockerfile 即可将源代码转换为容器映像的方法。  
Buildpacks 为开发人员提供了一种使用容器映像的便捷方式，而无需考虑构建它们所带来的复杂性。  
您可以创建自己的 Buildpack，也可以使用多个供应商提供的 Buildpack。  
构建包内置于 Cloud Run 中，用于支持基于源代码的部署工作流。

### Builders
![](../images/buildpack-builder.png)  
构建包在称为构建器的 OCI 映像中分发和执行。每个构建器可以有一个或多个构建包。  
生成器将源代码转换为容器映像。buildpack 执行生成和打包容器映像的实际工作。  
如果构建器开始处理源目录，它将执行构建包的两个阶段：检测阶段，检测阶段。

![](../images/buildpack-builder-001.png)  
在构建器运行检测阶段后，合适的构建包会激活并执行构建，而其他构建包则不会。

![](../images/buildpack-pack.png)  
使用命令行工具“pack”，您可以使用构建器将源代码转换为容器映像。

### Builders 的选择
Paketo Buildpacks：这是一个 Cloud Foundry Foundation 项目，致力于维护供应商中立的治理。  
Heroku Buildpacks：Heroku 是一个众所周知的平台即服务产品，可以轻松构建云原生应用程序。  
Google Cloud 的 buildpack 内置于 Cloud Run 中。

### Google Cloud 的构建包
App Engine、Cloud Functions 和 Cloud Run 在内部使用 Google Cloud 的构建包。  
Google Cloud 的构建包构建器支持用 Go、Java、Node.js、Python 和 .NET Core 编写的应用程序。  
您可以将源代码和容器映像部署到 Cloud Run。Cloud Run 使用 Google Cloud 的 buildpack 构建源代码。  

### 记得
* Buildpack 是一种无需编写 Dockerfile 即可从源代码创建容器映像的方法。
* 构建包在称为构建器的 OCI 映像中分发和执行。每个构建器可以有一个或多个构建包。
* 构建器可以支持以多种语言编写的源代码。
* 将命令行工具包与构建器结合使用，将源代码转换为容器映像。

## 持续集成和交付 （CI/CD） 的工具
### Skaffold
* 用于编排应用程序代码的持续开发、持续集成 （CI） 和持续交付 （CD） 的工具。
* 提供用于创建 CI/CD 管道的构建基块
* 使用可移植的声明性配置

### Artifact Registry
* 一种 Google Cloud 服务，用于存储和管理容器映像等软件工件。
* 与 Cloud Build 集成。

### Cloud Build
* 在 Google Cloud 上执行的服务。
* 从各种存储库或云存储空间导入源代码。
* 生成 Docker 容器或 Java 存档等工件。
* 使用构建配置可以：
  * 获取依赖项。
  * 运行单元和集成测试。
  * 执行静态分析。
  * 使用构建工具创建工件。

#### 构建过程
* 构建容器映像的过程是完全自动的，不需要你直接输入。
* 必须为您的项目启用 Cloud Build API。
* 构建过程中使用的所有资源都会在您自己的用户项目中执行，并且您可以通过 Cloud Logging 访问所有构建日志。

#### Cloud Build 的功能
* 使用任何编程语言编写代码。
* 使用构建配置文件。
* 与不同的源代码存储库集成。
* 自动生成、测试和部署代码。
* 将构建项目存储在不同的注册表和存储系统中。
* 部署到热门平台。

#### 云构建步骤
* 说明是作为一组步骤编写的。每个步骤都必须包含一个名称字段，该字段指定云构建器，云构建器是运行常用工具的容器映像。
* 步骤的 args 字段采用参数列表并将其传递给构建器。args 列表中的值用于访问构建器的入口点。如果生成器没有入口点，则 args 列表中的第一个元素将用作入口点。

#### 使用 Cloud Build 运行构建
1. 将您的应用代码和当前目录中的其他文件上传到 Cloud Storage。
2. 在指定区域中启动生成。
3. 使用指定名称标记图像。
4. 将生成的映像推送到 Artifact Registry。

#### Cloud Build 触发器
* 使用 Cloud Build 触发器自动运行构建。
* 可以在以下位置对源代码进行更改： ○ 云源存储库 ○ GitHub ○ Bitbucket
* 需要 Dockerfile 或 Cloud Build 配置文件。

#### 创建 Cloud Build 触发器
* 触发器名称、描述和云区域
* 触发事件
* 源存储库和分支
* 构建配置
* 服务帐户电子邮件

#### 其他类型的 Cloud Build 触发器
* 手动触发器
* Pub/Sub 触发器
* Webhook 触发器

## 构建和保护容器时的一些最佳实践
### 容器映像大小
![](../images/container-image-size.png)  
![](../images/container-image-size-001.png)  
该映像包含构建软件所需的系统包。甚至包括 Debian 软件包管理器 apt-get，因此您可以安装更多的系统软件包。  
此基础映像更适合于构建，而不是运行软件。在生产环境中，出于安全原因，映像越小越好。其他系统软件包中可能存在安全漏洞。

### 使用 Distroless 提高安全性和图像大小
![](../images/container-image-size-improve.png)  
我们使用 Distroless 项目中的映像来查看此过程，该映像针对运行应用程序进行了优化，因为它仅包含应用程序及其运行时（而不是生成时）依赖项。

![](../images/container-image-size-improve-dockerfile.png)  
FROM 指令后跟 COPY 指令，该指令将应用程序从先前暂存的映像拉取到活动阶段。

![](../images/container-image-build-by-multi-stage.png)  
使用多阶段生成创建最小容器映像。

### 记得
* 基础映像中充斥着运行应用程序不需要的包。
* Distroless 是一个提供最小运行时容器映像的项目。
* 如果重复 FROM 指令，则会创建多阶段生成。
* 若要完成生成，请将应用程序及其依赖项复制到最后阶段。

### 进程和信号处理
* 使用 Dockerfile 中的 CMD 或 ENTRYPOINT 指令启动容器应用程序进程。
  * 允许进程接收信号。
  * 启用应用程序在终止时正常关闭。
* 在应用程序代码中注册和实现信号处理程序。

### Docker 构建缓存
![](../images/container-docker-build-cache.png)  
生成容器映像时，Docker 会逐步执行 Dockerfile 中的指令，按指定顺序执行这些指令。每条指令都会在生成的图像中创建一个图层。对于每条指令，Docker 都会在其缓存中查找可重用的现有映像层。

只有当之前的所有构建步骤都使用了该缓存时，Docker 才能将其构建缓存用于映像。通过将涉及频繁更改的生成步骤放置在 Dockerfile 的底部，可以利用 Docker 生成缓存实现更快的生成。

由于通常会为源代码的每个新版本生成新的 Docker 映像，因此请尽可能晚地在 Dockerfile 中将源代码添加到映像中。

在此示例中，如果 STEP 1 涉及更改，Docker 只能重用 FROM debian：11 步骤中的层。如果 STEP 3 涉及更改，Docker 还可以重用 STEP 1 和 STEP 2 的层。

### 更多最佳实践
* 应尽可能少地保留容器映像中的内容，最好只保留应用，并删除任何不必要的工具或实用工具。这样可以减少应用的攻击面，并保护应用免受攻击者的潜在伤害。
* 若要防止攻击者使用包管理器（如 apt-get）修改容器映像中 root 拥有的文件，请避免在容器内以 root 用户身份运行应用。您还必须禁用或卸载 sudo 命令。此外，请考虑以只读模式启动容器。
* 构建较小的图像以减少图像上传和下载时间。映像越小，节点下载它的速度就越快。通过在 Dockerfile 的 FROM 指令中引用较小的基础映像，可以控制生成的容器映像的整体大小。
* 只需下载一次每个基础映像，即可为组织内的开发人员提供一组通用的标准基础映像。初始下载后，只需要使每个容器映像唯一的层，从而减少构建开发人员容器映像所需的时间。

### 漏洞扫描
![](../images/container-vulner-scanning.png)  
容器分析是一项服务，可为 Google Cloud 上的容器提供漏洞扫描和元数据存储服务。扫描服务对 Artifact Registry 中的映像执行漏洞扫描，然后存储生成的元数据，并使其可通过 API 使用。

启用后，此服务可以自动扫描容器映像，并在将新映像推送到 Artifact Registry 时触发。使用按需扫描 API，您还可以对存储在这些注册表中或本地存储的容器映像启用手动扫描。

### 自动修补
* 将映像存储在 Artifact Registry 中并启用漏洞扫描。
* 配置作业或使用 Pub/Sub 获取漏洞通知。
* 使用可用的修复程序触发映像的重建。
* 使用持续部署过程，将重新生成的映像部署到过渡环境。
* 测试映像，并触发将映像部署到生产环境。

### 按需扫描
* 授予默认的 Cloud Build 服务帐户 On-Demand Scanning 管理员 IAM 角色。
* 要扫描映像中的漏洞，运行 gcloud artifacts docker images scan 命令。
* 如果发现具有指定严重性级别的漏洞，请退出生成。

# Cloud Run 和 Google Kubernetes Engine 简介

# 课程回顾