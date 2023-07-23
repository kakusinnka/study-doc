# 课程信息
## 目标
* 讨论什么是云以及为什么它是技术和商业游戏规则的改变者。
* 描述用户与 Google Cloud 交互的不同方式。
* 探索 Google Cloud 中的不同计算选项。

# 课程介绍
略

# 那么，云到底是什么？
## 介绍
完成第一个模块后，您应该能够确定云是什么以及它对技术和业务的影响。
这意味着您将：
1. 探索云计算。
2. 比较和对比物理、虚拟和云架构。
3. 区分基础设施即服务 (IaaS)、平台即服务 (PaaS) 和软件即服务 (SaaS)。
4. 了解 Google Cloud 计算、存储、大数据和机器学习服务。
5. 并检查 Google 网络及其如何为云计算提供支持。

## 云计算
云计算是一种使用信息技术 (IT) 的方式，具有这五个同样重要的特征：
1. 客户获得按需和自助服务的计算资源。
2. 客户可以从任何有连接的地方通过互联网访问这些资源。
3. 这些资源的提供者拥有大量资源，并将它们分配给该资源池中的用户。
4. 资源具有弹性——这意味着资源可以根据需要增加或减少，因此客户可以灵活地使用。
5. 客户只需按使用量付费，或按使用量预订。

## 云与传统架构
在本节中，我们将探讨云与传统架构的比较。为了理解这一点，我们需要回顾一些历史。  
云计算的趋势始于称为托管的第一波浪潮。托管为用户提供了租赁物理空间的财务效率，而不是投资数据中心房地产。  
当今的虚拟化数据中心是第二次浪潮，虚拟化数据中心的组件与托管计算的物理构建块（服务器、CPU、磁盘、负载平衡器等）相匹配，但现在它们是虚拟设备。  
容器的架构是一种完全自动化、弹性的第三波云，由自动化服务和可扩展数据的组合组成。服务自动供应和配置用于运行应用程序的基础设施。  

## IaaS、PaaS 和 SaaS
* 基础架构即服务（也称为 IaaS）是一种通过互联网以服务的形式按需提供具有高扩缩能力的计算资源的服务。这样企业就无需自行采购、配置或管理基础架构，而且只需要为实际使用的资源付费。
* 平台即服务 (PaaS) 是一个完整的云环境，提供开发者构建、运行和管理应用所需的一切，从服务器和操作系统到所有网络、存储、中间件、工具等。
* SaaS 应用程序未安装在您的本地计算机上；它们作为服务在云中运行，并由最终用户直接通过互联网使用。

## 谷歌云构架
您可以将 Google Cloud 基础架构视为三层：
* 基础层是网络和安全，为支持所有 Google 基础设施和应用程序奠定了基础。
* 下一层是计算和存储。谷歌云将计算和存储分开或解耦，这样它们就可以根据需要独立扩展。
* 顶层是大数据和机器学习产品，使您能够执行摄取、存储、处理和交付业务洞察、数据管道和机器学习模型的任务。

## 概括
略

# 从一个平台开始
## 介绍
我们将探索与 Google Cloud 交互的不同方式：
1. 探索 Google Cloud 控制台。
2. 检查项目如何成为启用和使用 Google Cloud 服务的基础。
3. 了解 Google Cloud 中的结算方式。
4. 安装并配置云SDK。
5. 认识使用 Cloud Shell 和 Cloud Shell 代码编辑器的不同用例。
6. 探索 API 的工作原理。
7. 通过移动设备管理 Google Cloud 服务。

## Google Cloud 控制台
实际上有四种方式可以访问 Google Cloud 并与之交互：
* Google Cloud 控制台
* Cloud SDK & Cloud Shell
* API 
* Cloud 移动应用

Google Cloud 控制台是 Google Cloud 的图形用户界面 (GUI)，可帮助您在简单的基于 Web 的界面中部署、扩展和诊断生产问题。  
使用控制台，您可以轻松找到资源、检查其运行状况、对其进行完全管理控制，并设置预算以控制在其上的支出。  
该控制台还提供了一个搜索工具，可以在浏览器中快速查找资源并通过 SSH（即安全外壳协议）连接到实例。  

## 了解项目
Google Cloud 层次结构由四个级别组成，从下往上依次为：资源、项目、文件夹和组织节点。  
项目是启用和使用 Google Cloud 服务的基础，例如管理 API、启用计费、添加和删除协作者以及启用其他 Google 服务。  
每个项目都是一个单独的部分，每个资源都属于一个项目。  
项目可以有不同的所有者和用户，因为它们是单独计费和管理的。  
每个 Google Cloud 项目都具有三个标识属性：项目 ID、项目名称和项目编号。
* 项目 ID 是由 Google 分配的全球唯一标识符，创建后无法更改——它是不可变的。项目 ID 在不同的上下文中使用，以告知 Google Cloud 要使用的确切项目。
* 项目名称是用户创建的。它们不必是唯一的，并且可以随时更改，因此它们不是一成不变的。
* oogle Cloud 还为每个项目分配一个唯一的项目编号。

## 谷歌云结算
计费是在项目级别建立的。这意味着，当您定义 Google Cloud 项目时，您会将结算帐号关联到该项目。  
您将在此计费帐户中配置所有计费信息，包括您的付款选项。  
一个结算帐号可以关联到零个或多个项目，但未关联到结算帐号的项目只能使用免费的 Google Cloud 服务。  
怎样才能确保不会意外地产生巨额 Google Cloud 账单？
* 您可以在计费帐户级别或项目级别定义预算。
* 要在成本接近您的预算限额时收到通知，您可以创建警报。
* 报告是 Google Cloud 控制台中的一个可视化工具，可让您根据项目或服务监控支出。
* Google Cloud 还实现了配额，旨在防止由于以下原因导致资源过度消耗：错误或恶意攻击，保护帐户所有者和整个 Google Cloud 社区。
* 配额有两种类型：费率配额和分配配额。两者都应用于项目级别。
  * 费率配额在特定时间后重置。
  * 分配配额控制您的项目中可以拥有的资源数量。

## 安装并配置云SDK
[Cloud SDK](https://cloud.google.com/sdk?hl=zh-cn) 是一组命令行工具，可用于管理 Google Cloud 上托管的资源和应用。

## Cloud Shell
Cloud Shell 提供直接从浏览器对云资源的命令行访问。它是一个基于 Debian 的虚拟机，具有 5 GB 的持久主目录，可以轻松管理 Google Cloud 项目和资源。  
借助 Cloud Shell，Cloud SDK gcloud 命令和其他实用程序始终已安装、可用、最新且经过完全身份验证。  
从终端窗口中，您可以启动 Cloud Shell 代码编辑器，借助 Cloud Shell 代码编辑器，您可以在 Web 浏览器中实时编辑 Cloud Shell 环境中的文件。

## 实验室简介：Google Cloud 实践实验室之旅
在本实验中，您将了解 Qwiklabs 平台并能够识别实验室环境的关键功能。

## Qwiklabs 和 Google Cloud 导览 (GSP282)
### 概览
你将学到什么，在本实验中，您将了解以下内容：
* 实验室平台以及如何识别实验室环境的关键特征
* 如何使用特定凭据访问云控制台
* Google Cloud 项目，并找出有关这些项目的常见误解
* 如何使用 Google Cloud Navigation 菜单来识别 Google Cloud 服务的类型
* 基本角色，并使用 Cloud IAM 服务检查特定用户可用的操作
* API 库，并检查其主要功能

### Qwiklabs 基础知识
略

### 访问 Cloud Console
略

### Cloud Console 中的项目
Google Cloud 项目是一种用来组织和整理 Google Cloud 资源的实体。项目中通常包含各种资源和服务，例如，可能会包含一个虚拟机池、一组数据库，以及将它们彼此连接起来的网络。项目中还会包含一些设置和权限，用以指定安全规则以及哪些人有权访问哪些资源。  

### 导航菜单和服务
略

### 角色与权限
Google Cloud 提供了一组权限和角色，用以界定哪些人有权访问哪些资源。

### API 和服务
略

### 结束实验
略

### 恭喜！
略

## 实验室简介：Cloud Shell 和 gcloud 入门
您将了解如何使用 gcloud 命令行通过 Cloud Shell 连接到 Google Cloud 上托管的计算资源。

## Cloud Shell 和 gcloud 入门(GSP002)
### 概览
利用 Cloud Shell，您可以通过命令行访问托管在 Google Cloud 中的计算资源。Cloud Shell 是一款基于 Debian 的虚拟机，拥有 5 GB 的永久性主目录空间，可让您轻松管理 Google Cloud 项目和资源。Cloud Shell 中预装了 gcloud 命令行工具和您需要的其他实用程序，便于您快速上手。

### 初始设置
略

### 任务 1：配置环境
略

### 任务 2：过滤命令行输出结果
略

### 任务 3：连接到虚拟机实例
使用 gcloud compute 可以轻松连接到您的实例。 gcloud compute ssh 命令提供一个封装了 SSH 的容器，该容器负责处理身份验证以及将实例名称映射到 IP 地址。  
ssh-keygen 是 SSH 协议中用于生成和管理密钥对的实用工具，它是保证SSH连接安全性的重要组成部分，也是实现无密码登录的关键工具。

### 任务 4：更新防火墙
为确保能够正常通信，需要执行以下操作：
```
# 向虚拟机添加标记
gcloud compute instances add-tags gcelab2 --tags http-server,https-server
# 为 http 网络流量添加防火墙规则
gcloud compute firewall-rules create default-allow-http --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:80 --source-ranges=0.0.0.0/0 --target-tags=http-server
```

### 任务 5：查看系统日志
略

### 检验您的掌握情况
略

### 恭喜！
略

## Google Cloud APIs
访问 Google Cloud 的第三种方式是通过应用程序编程接口 (API)。  
Google Cloud 控制台包含一个名为 [Google API Explorer](https://developers.google.com/apis-explorer?hl=zh-cn) 的工具，该工具显示可用的 API 以及版本。  
Google 提供了多种流行语言的 Cloud 客户端和 Google API 客户端库，从而减轻了从代码中调用 Google Cloud 的繁琐任务。  

## 云控制台移动应用程序
访问 Google Cloud 的第四种也是最后一种方式是通过 Cloud Mobile App。  
Cloud 移动应用让您可以直接从移动设备管理 Google Cloud 上运行的服务。  

## 总结
略

# 使用 Google Cloud 构建您的应用
计算：探索 Google Cloud 中的计算选项

## 介绍
在本模块中，您将了解如何直接在 Google Cloud 中构建应用。这意味着您将：
* 探索云计算选项的作用。
* 了解如何构建和管理虚拟机。
* 检查使用自动缩放构建弹性应用程序。
* 利用 App Engine 探索 PaaS 选项。
* 检查使用 Cloud Functions 构建事件驱动的服务。
* 使用 Google Kubernetes Engine 识别容器化和编排应用程序。
* 确定使用 Cloud Run 开发和部署可扩展的容器化应用程序。

## 云中的计算选项
让我们从第一个主题开始，即云中的计算选项。Google Cloud 提供涵盖不同使用选项的各种计算服务。
* 对于需要应用程序专用资源的一般工作负载，Compute Engine 是一个不错的选择。
* 如果您正在寻找平台即服务，App Engine 是一个不错的选择。
* Cloud Functions 提供了一个无服务器选项，用于根据某种事件触发代码运行。
* 要在托管 Kubernetes 平台上运行容器，您可以利用 GKE。
* Cloud Run 是一个完全托管的无服务器平台，可让您开发和部署高度可扩展的容器化应用程序。

## 使用 Compute Engine 探索 IaaS
使用 Google Cloud 的 IaaS 解决方案：Compute Engine 构建和部署应用程序。  

## 实验室简介：创建虚拟机
略

## 创建虚拟机 - Creating a Virtual Machine (GSP001)
### 概览
您将执行的操作：
* 使用 Cloud 控制台创建虚拟机。
* 使用 gcloud 命令行创建虚拟机。
* 部署网络服务器并将其连接至虚拟机。

### 设置
略

### 任务 1. 通过 Cloud 控制台创建一个新实例
略

### 任务 2. 安装 NGINX Web 服务器
略

### 任务 3. 使用 gcloud 创建一个新实例
略

### 任务 4. 知识测验
略

### 恭喜！
略

## 通过自动缩放配置弹性应用程序
您可以使用一组预定义的机器类型或创建您自己的自定义机器类型。为此，Compute Engine 具有一项称为自动缩放的功能，可以根据负载指标向应用程序添加或删除虚拟机。

## 使用 App Engine 探索 PaaS
您将探索 App Engine 如何运行您的应用程序，而无需您管理基础架构。App Engine 允许您在完全托管的无服务器平台上构建高度可扩展的应用程序。  
那么它是怎样工作的：
* 借助 App Engine，您可以选择流行的编码语言、库和框架来开发应用程序，使用您熟悉的工具，然后根据需求自动配置服务器并扩展应用程序实例。
* App Engine 还提供内置服务和 API，例如 NoSQL 数据存储、Memcache、负载平衡、运行状况检查、应用程序日志记录以及大多数应用程序常用的用户身份验证 API。
* App Engine 提供软件开发工具包或 SDK，帮助您在本地计算机上开发、部署和管理应用程序。
* 每个 SDK 包括：
  * App Engine 可用的所有 API 和库
  * 一个模拟的安全沙箱环境，可模拟所有本地计算机上的 App Engine 服务
  * 以及用于将应用程序上传到云并管理不同版本的部署工具。
* SDK 在本地管理您的应用程序，Google Cloud 控制台在生产环境中管理您的应用程序。
* 使用 Google Cloud 控制台的网络界面创建新应用、配置域名、更改应用程序的实时版本、检查访问和错误日​​志等。

App Engine 环境有两种类型：标准环境和灵活环境。
* 第一个是 App Engine 标准环境，它基于在 Google 基础设施上运行的容器实例。容器预先配置了受支持语言和版本的标准化列表中的运行时，其中包括支持 App Engine 标准 API 的库。
* 标准环境功能包括：
  * 具有查询、排序和事务功能的持久存储。
  * 自动缩放和负载平衡。
  * 异步任务队列，用于在请求范围之外执行工作。
  * 计划任务，用于在指定时间或定期间隔触发事件。
  * 以及与其他 Google Cloud 服务和 API 的集成。
* 使用标准环境有几个要求：
  * 必须使用指定版本的Java、Python、PHP、Go、Node.js、Ruby。
  * 您的应用程序必须符合依赖于运行时的沙箱约束。
* 标准环境工作流程通常遵循以下三个步骤：
  * 首先，在本地开发并测试 Web 应用程序。
  * 其次，SDK 用于将应用程序部署到 App Engine。
  * 第三，App Engine 扩展应用程序并为其提供服务。
* App Engine 还提供了灵活的环境。如果标准环境的沙箱模型对您来说限制太多，灵活环境可以让您指定 Web 应用程序将在其中运行的容器类型。此选项允许应用程序在 Google Cloud 的 Compute Engine 虚拟机上的 Docker 容器内运行。在这种情况下，App Engine 会为您管理 Compute Engine 计算机。
* 这意味着：
  * 对实例进行健康检查，根据需要进行修复，并与项目中的其他模块实例共置。
  * 关键的、向后兼容的更新会自动应用于底层操作系统。
  * VM 实例会根据项目中的设置按地理区域自动定位。
  * VM 实例每周重新启动一次。
  * 灵活的环境支持微服务、授权、SQL 和 NoSQL 数据库、流量分割、日志记录、搜索、版本控制、安全扫描、Memcache 和内容交付网络。
  * App Engine 灵活的环境使用户还可以从自定义配置和库中受益。
  * 此外，App Engine 灵活环境允许您使用 Dockerfile 自定义虚拟机的运行时和操作系统。

那么，这两种环境相比如何：
[两种环境之间的差异](https://cloud.google.com/appengine/docs/the-appengine-environments?hl=zh-cn#compare_high-level_features)

由于 App Engine 使用 Docker 容器，您可能想知道 App Engine 与 Google Kubernetes Engine 相比如何。  
App Engine 标准环境适合希望服务能够最大程度地控制其 Web 和移动应用程序的部署和扩展的用户。  
然而，Google Kubernetes Engine 为应用程序所有者提供了 Kubernetes 的全部灵活性。  
App Engine 灵活环境介于两者之间。

## 实验室简介：App Engine：Qwik Start - Python
略

## App Engine：Qwik Start - Python (GSP067)
### 概览
App Engine 允许开发人员专注于做他们最擅长的事情，编写代码，而不是代码运行在什么上。  
开发人员不必担心操作系统、Web 服务器、日志记录、监控、负载平衡、系统管理或扩展，因为 App Engine 会处理所有这些问题。  

### 设置和要求
略

### 任务 1. 启用 Google App Engine 管理 API
略

### 任务 2. 下载 Hello World 应用程序
略

### 任务 3. 测试应用程序
```
# 在开发App Engine应用程序时，使用dev_appserver.py可以模拟App Engine运行时环境，让开发人员可以在本地进行开发、测试和调试。
# 在安装Google Cloud SDK后，dev_appserver.py将被自动安装，并且可以在命令行中直接使用。
dev_appserver.py app.yaml
```

### 任务 4. 进行一些改变
略

### 任务 5. 部署您的应用程序
```
gcloud app deploy
```

### 任务 6. 查看您的部署
```
gcloud app browse
```

### 任务 7. 测试您的知识
略

## 事件驱动程序 - Cloud Functions
Cloud Functions 是无服务器代码，可让您根据某些事件运行它。  
Cloud Functions 是一种轻量级、基于事件的异步计算解决方案，允许您创建小型、单一用途的函数来响应云事件，而无需管理服务器或运行时环境。  
您可以使用这些函数从小型业务逻辑构建应用程序。  
您还可以使用Cloud Functions连接和扩展云服务。  
来自 Cloud Storage 和 Pub/Sub 的事件可以异步触发 Cloud Functions，也可以使用 HTTP 调用来同步执行。  

## 实验室简介：Cloud Functions：Qwik Start - 命令行
您将使用 Cloud Shell 命令行创建简单的云函数、部署和测试函数以及查看日志。

## Cloud Functions：Qwik Start - 命令行 (GSP080)
### 概览
Cloud Functions 是一种用于构建和连接云端服务的无服务器执行环境。借助 Cloud Functions，您可以编写单一用途的简单函数，并将这些函数与您的云基础架构和服务发出的事件进行关联。当所监控的事件发生时，您的 Cloud Functions 函数就会被触发。您的代码将在全代管式环境中执行。您无需预配任何基础架构，也不必费心管理任何服务器。

Cloud Functions 函数可以使用 Node.js、Python 和 Go 编写，并可在相应语言版本的运行时中执行。您可以在任何标准的 Node.js 运行时环境中运行自己的 Cloud Functions 函数，这样便于轻松进行移植和本地测试。

### 连接和扩展云端服务
Cloud Functions 提供了一个逻辑连接层，让您可以编写代码来连接和扩展云端服务。您可以监听以下事件并对其做出响应：Cloud Storage 中上传了文件、日志更改或收到有关 Cloud Pub/Sub 主题的消息。Cloud Functions 可增强现有云端服务，让您能够通过任意编程逻辑来满足越来越多使用场景的需要。Cloud Functions 可以访问 Google 服务帐号凭据，因此能够顺畅通过大多数 Google Cloud 服务（包括 Datastore、Cloud Spanner、Cloud Translation API 和 Cloud Vision API）以及其他许多服务的身份验证。此外，许多 Node.js 客户端库都支持 Cloud Functions，从而使这些集成变得更加简单。

### 事件和触发器
云事件是指在云环境中发生的事件。具体的示例包括：数据库中发生数据变更、存储系统中添加了文件，或有新的虚拟机实例正在创建。

无论您是否选择响应事件，这些事件都会发生。您可以使用触发器创建对事件的响应。触发器是一种声明，用于表明您对某个事件或一系列事件感兴趣。通过将函数与触发器绑定，您就可以捕获事件并执行事件处理操作。

### 无服务器
使用 Cloud Functions 后，您无需再管理服务器、配置软件、更新框架和修补操作系统。软件和基础架构完全由 Google 代管，您只需添加代码即可。此外，系统会自动预配资源来响应事件。也就是说，对一个函数的调用次数哪怕从一天几次增加到数百万次，也无需您执行任何操作。

### 使用场景
异步工作负载（例如轻量级 ETL）或云端自动化（例如触发应用构建）不再需要有自己的服务器，也不再需要开发者对其进行绑定。您只需部署 Cloud Functions 函数，使其绑定到您期望的事件，就大功告成了。

### 设置
略

### 创建一个函数
这段代码定义了一个简单的Cloud Function，用于处理来自Google Cloud Pub/Sub的消息。它将消息中的Base64编码数据解码，并打印出一个带有解码后数据的日志信息。
```
/**
* Background Cloud Function to be triggered by Pub/Sub.
* This function is exported by index.js, and executed when
* the trigger topic receives a message.
*
* @param {object} data The event payload.
* @param {object} context The event metadata.
*/
exports.helloWorld = (data, context) => {
const pubSubMessage = data;
const name = pubSubMessage.data
    ? Buffer.from(pubSubMessage.data, 'base64').toString() : "Hello World";
console.log(`My Cloud Function: ${name}`);
};
```
### 创建 Cloud Storage 存储桶
略

### 部署函数
略

### 测试函数
略

### 查看日志
略

### 检验您的掌握情况
略

### 恭喜！
略

