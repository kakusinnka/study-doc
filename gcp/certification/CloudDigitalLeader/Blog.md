## [在 BigQuery 按需定价和统一费率定价之间进行选择](https://cloud.google.com/blog/products/data-analytics/choosing-bigquery-pricing?hl=en)

BigQuery 是 Google Cloud 完全托管的企业数据仓库。我们将存储和计算解耦，因此存储和计算的成本也解耦了。我们将在本文中仅讨论计算成本。  
您可以使用纯粹的即用即付模型，您只需为用于查询数据的计算付费。在这种即用即付模型（也称为按需定价）中，您需要根据查询扫描的字节数进行计费。在固定费率模式中，您每月为 BigQuery 服务中的专用资源支付固定金额，并且可以扫描任意数量的数据。  
借助 BigQuery 沙盒，您可以在迁移数据仓库之前免费尝试查询、测试性能或尝试标准 SQL。  
BigQuery 的按需模型为每个 Google Cloud 项目提供多达 2,000 个插槽，并且在容量可用时能够突破这一限制。槽是 BigQuery 的计算能力单位，它们会在查询执行时动态调度。如上所述，当您的查询执行时，它们将扫描数据。您将根据在按需计费模型中扫描的字节数进行计费。BigQuery 槽是 BigQuery 执行 SQL 查询的虚拟 CPU。  
在固定费率模型中，您可以决定要预留多少个插槽，并且每月为这些资源支付固定费用。您可以选择是预留一分钟的时段，还是按月预留，或者承诺一年。在此模型中，您不再根据扫描的字节数付费。可以将其视为一个无限查询计划。  

## [将您的组织与 Google Cloud Platform 资源层次结构进行映射](https://cloud.google.com/blog/products/gcp/mapping-your-organization-with-the-Google-Cloud-Platform-resource-hierarchy/?hl=en)

组织、项目和文件夹构成了 GCP 资源层次结构。您可以将层次结构视为传统操作系统中的文件系统。它提供所有权，因为每个 GCP 资源都有一个控制其生命周期的父资源。它提供分组功能，因为可以将资源组装到逻辑上代表服务、应用程序或组织实体（例如组织中的部门和团队）的项目和文件夹中。此外，它还提供了访问控制和配置策略的“脚手架”，您可以将其附加到任何节点并沿层次结构传播，从而简化管理并提高安全性。  
下图显示了 GCP 资源层次结构的示例:  
![GCP 资源层次结构](./images/cloud-hierarchy.png)  
项目是第一级所有权、分组和政策附加点。另一方面，组织包含属于公司的所有资源，并提供集中可见性和控制的高级范围。在组织级别定义的策略由层次结构中的所有资源继承。在中间，文件夹可以包含项目或其他文件夹，并提供根据隔离要求组织和创建边界的灵活性。  
GCP 中组织资源时需要考虑以下一些标准：
* 隔离：您希望在哪里建立信任边界：在部门和团队级别，在应用程序或服务级别，还是在生产、测试​​和开发环境之间？使用文件夹及其嵌套层次结构和项目在云资源之间创建隔离。在层次结构的不同级别设置 IAM 策略，以确定谁有权访问哪些资源。
* 授权：如何平衡自治与集中控制？文件夹和 IAM 可帮助您建立分区，让开发人员能够更自由地进行创建和实验，并保留具有更严格控制的区域。
* 继承：继承如何优化策略管理？正如我们提到的，您可以在层次结构的每个节点定义策略并将其向下传播。 IAM 策略是累加性的。
* 共享资源：是否有需要在整个组织内共享的资源，例如网络、VM 映像、服务帐户？使用项目和文件夹为共享资源构建中央存储库，并将这些资源的管理权限仅限于选定的用户。使用最小权限原则允许其他用户访问。

## [Compute Engine 解释：选择正确的机器系列和类型](https://cloud.google.com/blog/products/compute/choose-the-right-google-compute-engine-machine-type-for-you?hl=en)

对于想要在 Google Cloud 中运行虚拟机 (VM) 的组织，Compute Engine 提供了多个机器系列可供选择，每个机器系列都适合特定的工作负载和应用程序。每个机器系列中都有一组机器类型，它们提供规定的处理器和内存配置组合。  
* 通用 (E2, N2, N2D) - 这些机器平衡了价格和性能，适合大多数工作负载，包括数据库、开发和测试环境、Web 应用程序和移动游戏。为了灵活性，通用机器是预定义的（具有预设数量的 vCPU 和内存），或者可以配置为自定义机器类型。自定义机器类型允许您独立配置 CPU 和内存，为您的应用程序找到适当的平衡，因此您只需为您需要的部分付费。
* 计算优化 (C2) - 这些机器在 Compute Engine 上提供最高的每个核心性能，并针对计算密集型工作负载进行了优化，例如高性能计算 (HPC)、游戏服务器和延迟敏感的 API 服务。
* 内存优化 (M1, M2) - 这些机器在我们的 VM 系列中提供最高的内存配置，单个实例高达 12 TB。它们非常适合内存密集型工作负载，例如 SAP HANA 等大型内存数据库和内存数据分析工作负载。
* 加速器优化 (A2) - 这些机器基于 NVIDIA Ampere A100 Tensor Core GPU。这些机器在单个虚拟机中拥有多达 16 个 GPU，适用于要求苛刻的工作负载，例如支持 CUDA 的机器学习 (ML) 训练和推理以及 HPC。

## [Google Cloud 推出 Vertex AI，一个平台，满足您所需的每一款机器学习工具](https://cloud.google.com/blog/products/ai-machine-learning/google-cloud-launches-vertex-ai-unified-platform-for-mlops?hl=en)

Vertex AI，这是一个托管机器学习 (ML) 平台，可帮助公司加速人工智能 (AI) 模型的部署和维护。Vertex AI 将 Google Cloud 服务整合在一起，在一个统一的 UI 和 API 下构建机器学习，以简化大规模构建、训练和部署机器学习模型的过程。Vertex AI 是一个单一平台，包含您所需的所有工具，使您能够管理数据、原型、实验、部署模型、解释模型并在生产中监控它们，而无需正式的 ML 培训。这意味着您的数据科学家不需要是机器学习工程师。借助 Vertex AI，他们有能力快速行动，但有了安全网，他们的工作始终是他们能够启动的。该平台有助于负责任的部署，并确保您更快地从测试和模型管理转向生产，并最终推动业务成果。

## [什么是顶点人工智能？开发者倡导者分享更多](https://cloud.google.com/blog/products/ai-machine-learning/vertex-ai-overview?hl=en)

Vertex AI 将 Google Cloud 现有的 ML 产品统一到一个环境中，以高效构建和管理 ML 项目的生命周期。它为不同模型类型的机器学习工作流程的每个步骤提供工具，以适应不同水平的机器学习专业知识。

## [AI 简化：使用 Vertex AI 管理 ML 数据集](https://cloud.google.com/blog/products/ai-machine-learning/vertex-ai-how-to-create-and-manage-data-sets?hl=en)

数据集是机器学习生命周期的第一步——开始时您需要数据，而且是大量数据。 Vertex AI 目前支持四种数据类型的托管数据集：图像、表格、文本和视频。  
图像数据集可让您执行以下操作：
* 图像分类——识别图像中的项目。
* 物体检测——识别图像中物体的位置。
* 图像分割——为图像中的像素级区域分配标签。

表格数据集使您能够执行以下操作：
* 回归——预测数值。
* 分类——预测与特定示例相关的类别。
* 预测——预测突发事件或需求的可能性。

使用文本数据集，您可以执行以下操作：
* 分类—为整个文档分配一个或多个标签。
* 实体提取 - 识别文档中的自定义文本实体，例如“太贵”或“很有价值”。
* 情绪分析——识别一段文本中表达的整体情绪，例如，客户是高兴、不安还是沮丧。

视频数据集可以：
* 分类 - 标记整个视频、镜头或帧。
* 动作识别 - 识别发生特定动作的视频剪辑。
* 对象跟踪 - 跟踪视频中的特定对象。

## [Google Cloud 上的 DevOps 和 CI/CD 说明](https://cloud.google.com/blog/topics/developers-practitioners/devops-and-cicd-google-cloud-explained?hl=en)

持续集成（CI）的核心是尽早且经常地获得反馈，这使得可以在开发过程的早期发现并纠正问题。通过 CI，您可以频繁地集成您的工作，通常是一天多次，而不是等待稍后进行大型集成。每个集成都通过自动构建进行验证，这使您能够尽快检测集成问题并减少下游问题。  
CD 是关于打包和准备软件，其目标是向用户提供增量更改。  
您的 CI/CD 管道应该支持：
* 打包源码
* 自动化单元和集成测试
* 一致的构建环境
* 部署到生产之前获得批准
* 蓝色/绿色和金丝雀推出

Cloud Build 是一个完全托管的 CI/CD 平台，可让您跨混合云和多云环境（包括虚拟机、无服务器、Kubernetes 和 Firebase）进行构建、测试和部署。 Cloud Build 可以从 Cloud Storage、Cloud Source Repositories、GitHub 或 Bitbucket 导入源代码；根据您的规范执行构建；并生成 Docker 容器映像或 Java 档案等工件。  
如果您完全在云原生环境中工作，那么您将需要使用 Cloud Code 来启动 CI/CD 管道。在您的 IDE 中使用 Cloud Code；它附带的工具可帮助您快速轻松地编写、运行和调试云原生应用程序。然后将您的代码推送到 Cloud Build 进行构建过程，将其打包到 Artifact Registry 中，并在 GKE 或 Cloud Run 上运行。  
​​Google Cloud Deploy（预览版）是一项托管的、固执己见的持续交付服务，使向 GKE 的持续交付变得更容易、更快、更可靠。它内置了安全控制，可以与您现有的 DevOps 生态系统集成。  
Cloud Shell Editor 由 Eclipse Theia IDE 平台提供支持，通过在线预配置的云开发环境扩展了 Cloud Shell，其中包括：
* 适用于 Kubernetes 和无服务器的本地模拟器
* 用于使用云原生应用程序的命令行工具

## [了解 Compute Engine 的新托管实例组更新程序](https://cloud.google.com/blog/products/gcp/meet-compute-engines-new-managed-instance-group-updater/?hl=en)

Google Compute Engine 的一个关键功能是托管实例组，它允许您将相同实例的集合作为一个单元进行管理，以快速部署新虚拟机并确保它们配置一致。使您可以比以往更轻松地更新实例上的软件、修补和更新它们以及推出分阶段和测试部署。  
具体来说，新的托管实例组更新程序允许您：
* 以编程方式将您的实例从一个实例模板更新为另一个实例模板
* 指定一次更新多少个实例：一个、多个或全部
* （临时）部署额外实例以在更换旧实例时维持容量
* 重新启动或重新创建托管实例组中的所有实例而不更改模板
* 通过配置实例更新之间的暂停来控制部署速率

## [Bigtable 与 BigQuery：有什么区别？](https://cloud.google.com/blog/topics/developers-practitioners/bigtable-vs-bigquery-whats-difference?hl=en)

从较高的层面来看，Bigtable 是一个 NoSQL 宽列数据库，针对大量读取和写入进行了优化。Bigtable 是一个 NoSQL 宽列数据库。它针对低延迟、大量读取和写入以及大规模保持性能进行了优化。 Bigtable 用例具有一定的规模或吞吐量，具有严格的延迟要求，例如 IoT、AdTech、FinTech 等。  
BigQuery 是一个用于存储大量关系结构化数据的企业数据仓库。BigQuery 是一个用于大量关系结构化数据的企业数据仓库。它针对大规模、基于 SQL 的临时分析和报告进行了优化，这使得它最适合获得组织洞察力。

## [Cloud Functions 与 Cloud Run：何时使用其中之一](https://cloud.google.com/blog/products/serverless/cloud-run-vs-cloud-functions-for-serverless?hl=en)

我们发现无服务器工作负载往往属于两类之一：连接平台或运行服务。连接平台通常涉及编写执行单个任务并受益于简单性的离散代码段。另一方面，运行服务受益于自定义服务器配置的灵活性和执行多个任务的能力。  
我们利用 Cloud Functions 处理由 Cloud Storage、Eventarc 或 PubSub 等其他系统触发的短暂的、基于事件的操作，例如用于数据管道自动化。  
Cloud Functions 的例子：
* 转换数据并将其加载到 BigQuery 中。
* 创建由第三方（即 GitHub）调用的 Webhook。
* 使用 ML API 分析添加到数据库或存储桶的数据。

当需要进一步定制时，例如，当需要嵌入人工智能模型或需要更长时间地服务多个接口时，Cloud Run 就会发挥作用。  
许多应用程序示例可供您选择 Cloud Run：
* 任何基于 Web 的工作负载。
* 适用于移动应用或游戏的 REST 或 gRPC API。
* 内部自定义后台应用程序。