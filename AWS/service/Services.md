## AWS Systems Manager OpsCenter
OpsCenter 是一个专注于 **运维问题管理的工具** ，帮助团队快速识别、分析和解决问题，从而提升系统的可靠性和运维效率。

## AWS Cloud Map
AWS Cloud Map 是一项 **服务发现（Service Discovery）服务** ，专门用来帮助开发者在分布式系统或微服务架构中，轻松找到和连接动态变化的应用程序资源。

AWS Cloud Map 就像是一个动态的“资源目录”或“地址簿”，可以为你的应用程序提供资源的注册、命名和实时发现功能。

## Amazon Inspector
Amazon Inspector 是 AWS 提供的一项 **自动化的安全评估服务** ，用于帮助客户发现 AWS 环境中的安全漏洞和配置问题。它能够扫描运行在 AWS 上的资源（如 EC2 实例、容器镜像等），识别潜在的漏洞、暴露的网络访问权限以及不符合安全最佳实践的配置，并提供修复建议。

在 Amazon Inspector 中，单词 "Inspector" 的意思是 检查员 或 审查员，表示这个服务的主要功能是对 AWS 环境中的资源进行 检查、审查和评估。它的职责类似于一个安全检查员，负责扫描和发现潜在的安全漏洞或配置问题。

## Amazon Macie
Amazon Macie 是 AWS 提供的一项 **数据安全和隐私保护服务** ，通过机器学习（ML）和模式匹配技术，帮助用户自动发现、分类和保护存储在 Amazon S3 中的敏感数据（如个人身份信息 PII、财务数据或知识产权）。它可以识别数据泄露风险并提供详细的可操作建议，从而帮助企业满足数据隐私法规（如 GDPR、CCPA）的要求。

## Amazon GuardDuty
Amazon GuardDuty 是一项 **威胁检测服务** ，可持续监控、分析和处理您 AWS 环境中的 AWS 数据源和日志。 GuardDuty 使用威胁情报源（例如恶意 IP 地址和域名列表、文件哈希和机器学习 (ML) 模型）来识别 AWS 环境中的可疑活动和潜在的恶意活动。

## AWS Client VPN
AWS Client VPN 是一项 **完全托管的远程访问 VPN 服务** ，允许用户安全地连接到 AWS 和本地网络。它基于 OpenVPN 协议，使用户能够通过互联网从任何地方安全地访问 AWS 资源或本地资源。

这项服务主要用于为远程员工、分布式团队或需要安全访问 AWS 环境的用户提供便捷、可靠的 VPN 解决方案，而无需自行部署和管理 VPN 基础设施。

![Client VPN architecture](./images/client-vpn-001.png)

## AWS Site-to-Site VPN
AWS Site-to-Site VPN 是一项 AWS 提供的 安全网络服务，用于在用户的本地网络（如数据中心、办公室）与 AWS 云之间建立加密的虚拟专用网络（VPN）连接。通过 Site-to-Site VPN，用户可以安全地将本地环境与 Amazon Virtual Private Cloud (VPC) 或 AWS Transit Gateway 连接起来，从而构建混合云架构，实现数据的安全传输。

## AWS Client VPN 与 AWS Site-to-Site VPN 对比
| **对比维度**   | **AWS Site-to-Site VPN**            | **AWS Client VPN**                           |
| -------------- | ----------------------------------- | -------------------------------------------- |
| **主要用途**   | 连接本地网络与 AWS 云。             | 为远程用户提供安全访问 AWS 云的能力。        |
| **连接方式**   | 本地网络设备（如路由器）到 AWS 云。 | 用户设备（如笔记本电脑）到 AWS 云。          |
| **适用场景**   | 混合云架构、站点连接、灾难恢复。    | 远程办公、分布式团队、安全用户访问。         |
| **配置复杂度** | 较高，需要网络管理员配置本地设备。  | 较低，用户只需安装客户端并配置即可。         |
| **用户规模**   | 适合企业级网络，连接整个站点。      | 适合个人用户或分布式团队，支持大量用户连接。 |
| **安全性**     | 使用 IPsec 协议加密。               | 使用 OpenVPN 协议加密，支持用户身份验证。    |
| **典型用户**   | 企业 IT 团队、需要混合云的企业。    | 远程员工、分布式团队、需要灵活访问的用户。   |


## AWS Direct Connect
AWS Direct Connect 是 **一种网络服务，允许用户通过专用网络连接将其本地数据中心、办公室或托管环境直接连接到 AWS 云** 。通过 Direct Connect，用户可以绕过公共互联网，建立一条私密、低延迟、高带宽的专用连接，从而实现更高的网络性能、安全性和稳定性。

## Amazon Connect
Amazon Connect 是 AWS 提供的一项 **云端联络中心服务** ，旨在帮助企业轻松建立和管理客户服务中心。它是一种高度可扩展、经济高效且易于使用的解决方案，允许企业通过语音、聊天和其他渠道与客户进行互动。

Amazon Connect 的核心理念是简化联络中心的部署和运营，同时通过 AWS 的云服务提供高可用性、灵活性和智能化功能（如 AI 驱动的客户交互和分析）。它无需复杂的硬件或软件安装，用户可以快速启动并根据需求扩展。

## Amazon Transcribe
Amazon Transcribe 是 AWS 提供的一项 **自动语音识别（ASR）服务** ，能够将语音转换为文本。它利用先进的机器学习技术，支持多种语言的语音转录，帮助用户快速、高效地将音频或视频内容转换为可用的文本数据。

该服务被广泛应用于各种场景，如客户服务记录转录、字幕生成、会议记录自动化等，为企业和开发者提供了一种经济高效且易于集成的语音转文本解决方案。

## Amazon Polly
Amazon Polly 是 AWS 提供的一项 **文本转语音（Text-to-Speech, TTS）服务** ，能够将文本转换为自然流畅的语音。它使用先进的深度学习技术，支持多种语言和语音风格，帮助用户轻松构建语音驱动的应用程序。

Amazon Polly 的目标是通过生成高质量、自然的语音输出，为用户提供沉浸式的交互体验。它广泛应用于语音助手、语音播报、教育内容、无障碍技术等场景。

## Amazon Translate
Amazon Translate 是 AWS 提供的一项 **基于神经网络机器翻译（Neural Machine Translation, NMT）技术的云端翻译服务** ，能够以高质量和高速度将文本从一种语言翻译为另一种语言。它支持多种语言和语言对，帮助企业和开发者快速实现多语言内容的翻译和本地化。

## Amazon Textract
Amazon Textract 是 AWS 提供的一项 **基于机器学习的文档分析服务** ，能够自动从扫描的文档、图像或 PDF 文件中提取文本、表格、表单数据和其他结构化信息。与传统的光学字符识别（OCR）技术不同，Amazon Textract 不仅能够识别文本，还能理解文档的布局和内容结构，从而提取有意义的数据。

## Amazon Comprehend
Amazon Comprehend 是 AWS 提供的一项 **自然语言处理（Natural Language Processing, NLP）服务**，能够从非结构化文本中提取有意义的信息。它使用机器学习技术分析文本，识别情感、关键短语、实体、语言以及文本之间的主题关系，帮助用户将非结构化数据转化为可操作的洞察。

## CloudFront
CloudFront 是一种 **内容分发网络（CDN）服务** ，可以低延迟和高传输速度向全球客户安全地分发数据、视频、应用程序和 API。

## AWS Migration Hub
AWS Migration Hub 是 AWS 提供的一项集中式服务，旨在 **帮助用户规划、跟踪和管理应用程序迁移到 AWS 云的过程** 。通过 Migration Hub，用户可以在一个统一的界面中查看迁移进度，无论是使用 AWS 原生迁移工具还是第三方迁移工具，都能集中管理和监控。

Migration Hub 的主要目标是简化迁移流程，为用户提供全面的可见性，帮助企业更高效地将本地数据中心迁移到 AWS 云。

## AWS Application Migration Service（AWS MGN）
AWS Application Migration Service（AWS MGN） 是 AWS 提供的一项迁移服务，旨在 **帮助用户将本地数据中心、虚拟机或其他云平台上的应用程序迁移到 AWS 云** 。AWS MGN 通过自动化迁移流程，简化了迁移工作，并最大限度地减少了迁移中断时间。它支持将物理服务器、虚拟服务器（如 VMware、Hyper-V）和云端服务器迁移到 AWS，同时保持应用程序在迁移前后的运行状态一致。

## AWS Application Discovery Service
AWS Application Discovery Service 通过收集有关本地服务器和数据库的使用情况和配置数据，帮助您规划向 AWS 云的迁移。

## AWS CodeArtifact
AWS CodeArtifact 是 AWS 提供的一项 **完全托管的依赖包管理服务** ，用于存储、发布和共享软件包。它支持多种编程语言和构建工具（如 npm、Maven、PyPI 和 NuGet），帮助开发团队集中管理项目中的依赖项和软件包，同时确保版本一致性和安全性。

## AWS CodeBuild
AWS CodeBuild 是 AWS 提供的一项 **完全托管的持续集成（CI）服务，用于自动化代码的构建、测试和打包** 。它能够从代码存储库中获取源代码，执行编译、运行单元测试，并生成可部署的构建工件（如二进制文件或容器镜像）。CodeBuild 是无服务器的，用户无需管理构建服务器，AWS 会根据需要自动分配和扩展资源。

## AWS CodePipeline
AWS CodePipeline 是 AWS 提供的一项 **完全托管的持续集成与持续交付（CI/CD）服务** ，用于自动化代码的构建、测试和部署流程。通过 CodePipeline，开发团队可以快速实现从代码提交到生产环境的自动化发布，确保应用程序的高质量和快速交付。

## AWS Elastic Beanstalk
AWS Elastic Beanstalk 是一项由 Amazon Web Services (AWS) 提供的全托管平台即服务（PaaS），**用于快速部署和管理应用程序** 。它支持多种开发语言和框架，允许开发者专注于代码，而无需担心底层基础设施的配置、管理和扩展。

## AWS CodeCommit
AWS CodeCommit 是 AWS 提供的一项 **完全托管的源代码控制服务** ，支持团队安全地存储和管理代码、二进制文件或其他资产。它是基于 Git 的源代码管理工具，开发者可以像使用其他 Git 仓库（如 GitHub、GitLab、Bitbucket 等）一样使用 CodeCommit，但 CodeCommit 提供了更高的安全性、可扩展性和与 AWS 服务的深度集成。

## AWS Trusted Advisor
AWS Trusted Advisor 是 AWS 提供的一项 **实时建议服务，帮助用户优化其 AWS 环境的性能、成本、安全性、容错性和服务配额使用情况** 。它会根据 AWS 的最佳实践，自动分析用户的 AWS 资源，并提供优化建议，帮助用户更高效地使用 AWS 服务，同时降低成本并提高安全性。

## AWS Config
AWS Config 是一项 **完全托管的服务，用于持续评估、审核和记录 AWS 资源的配置变化** 。通过 AWS Config，用户可以跟踪 AWS 资源的配置历史，了解资源的当前状态，以及资源配置是否符合指定的合规性要求（如安全性、成本控制等）。它帮助用户实现资源的可视化管理、合规性检查和配置变更的自动化审计。

## Amazon CloudWatch
Amazon CloudWatch 是 AWS 提供的一项 监**控和管理服务，用于收集、分析和可视化 AWS 云资源及应用程序的性能和运行数据** 。通过 CloudWatch，用户可以实时监控资源的运行状态、设置警报、自动响应事件，并优化应用程序和基础设施的性能。

## AWS CloudTrail
AWS CloudTrail 是 AWS 提供的一项 **日志记录和监控服务，用于跟踪和记录 AWS 账户中的操作事件** 。CloudTrail 会记录所有对 AWS 服务的 API 调用，包括通过 AWS 管理控制台、命令行工具、SDK 和其他服务发起的操作。通过这些记录，用户可以进行安全分析、合规性检查、资源变更审计以及问题排查。

## [AWS Well-Architected Framework](./Well-ArchitectedFramework.md)
AWS Well-Architected Framework 是由 AWS 提供的 **一套云架构最佳实践指导原则，旨在帮助用户设计、构建和优化其在 AWS 云上的工作负载** 。通过 Well-Architected Framework，用户可以评估其架构的质量，识别潜在的改进点，并确保其架构能够满足业务需求，同时遵循高效、安全、可靠和经济的云架构设计原则。

## AWS Support
AWS Support 是 Amazon Web Services 提供的 **一套支持服务，旨在帮助客户更好地使用 AWS 平台，解决技术问题，优化云架构，并确保工作负载的高效运行** 。AWS Support 服务涵盖从基础技术支持到高级架构建议的广泛范围，适用于各种规模的企业和不同的技术需求。