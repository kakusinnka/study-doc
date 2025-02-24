## AWS Systems Manager OpsCenter
OpsCenter 是一个专注于 **运维问题管理的工具，帮助团队快速识别、分析和解决问题，从而提升系统的可靠性和运维效率**。

## AWS Cloud Map
AWS Cloud Map 是一项 **服务发现（Service Discovery）服务，专门用来帮助开发者在分布式系统或微服务架构中，轻松找到和连接动态变化的应用程序资源**。

AWS Cloud Map 就像是一个动态的“资源目录”或“地址簿”，可以为你的应用程序提供资源的注册、命名和实时发现功能。

## Amazon Macie
Amazon Macie 是 AWS 提供的一项 **数据安全和隐私保护服务** ，通过机器学习（ML）和模式匹配技术，帮助用户自动发现、分类和保护存储在 Amazon S3 中的敏感数据（如个人身份信息 PII、财务数据或知识产权）。它可以识别数据泄露风险并提供详细的可操作建议，从而帮助企业满足数据隐私法规（如 GDPR、CCPA）的要求。

## AWS Client VPN
AWS Client VPN 是一项 **完全托管的远程访问 VPN 服务** ，允许用户安全地连接到 AWS 和本地网络。它基于 OpenVPN 协议，使用户能够通过互联网从任何地方安全地访问 AWS 资源或本地资源。

这项服务主要用于为远程员工、分布式团队或需要安全访问 AWS 环境的用户提供便捷、可靠的 VPN 解决方案，而无需自行部署和管理 VPN 基础设施。

![Client VPN architecture](../images/client-vpn-001.png)

## AWS Site-to-Site VPN
AWS Site-to-Site VPN 是一项 AWS 提供的 **安全网络服务，用于在用户的本地网络（如数据中心、办公室）与 AWS 云之间建立加密的虚拟专用网络（VPN）连接**。通过 Site-to-Site VPN，用户可以安全地将本地环境与 Amazon Virtual Private Cloud (VPC) 或 AWS Transit Gateway 连接起来，从而构建混合云架构，实现数据的安全传输。

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

## AWS Transit(过境) Gateway
AWS Transit Gateway 是 AWS 提供的 **一项网络服务，用于在一个中心化网关中连接多个 Amazon Virtual Private Cloud (VPC)、本地数据中心和其他网络资源**。它简化了大规模网络架构的管理，提供高效、安全和可扩展的网络互联方式。

## AWS Direct Connect
AWS Direct Connect 是 **一种网络服务，允许用户通过专用网络连接将其本地数据中心、办公室或托管环境直接连接到 AWS 云** 。通过 Direct Connect，用户可以绕过公共互联网，建立一条私密、低延迟、高带宽的专用连接，从而实现更高的网络性能、安全性和稳定性。

# 机器学习
## Amazon Transcribe
Amazon Transcribe 是 AWS 提供的一项 **自动语音识别（ASR）服务，能够将语音转换为文本** 。它利用先进的机器学习技术，支持多种语言的语音转录，帮助用户快速、高效地将音频或视频内容转换为可用的文本数据。

该服务被广泛应用于各种场景，如客户服务记录转录、字幕生成、会议记录自动化等，为企业和开发者提供了一种经济高效且易于集成的语音转文本解决方案。

## Amazon Polly
Amazon Polly 是 AWS 提供的一项 **文本转语音（Text-to-Speech, TTS）服务，能够将文本转换为自然流畅的语音** 。它使用先进的深度学习技术，支持多种语言和语音风格，帮助用户轻松构建语音驱动的应用程序。

Amazon Polly 的目标是通过生成高质量、自然的语音输出，为用户提供沉浸式的交互体验。它广泛应用于语音助手、语音播报、教育内容、无障碍技术等场景。

## Amazon Translate
Amazon Translate 是 AWS 提供的一项 **基于神经网络机器翻译（Neural Machine Translation, NMT）技术的云端翻译服务** ，能够以高质量和高速度将文本从一种语言翻译为另一种语言。它支持多种语言和语言对，帮助企业和开发者快速实现多语言内容的翻译和本地化。

## Amazon Textract
Amazon Textract 是 AWS 提供的一项 **基于机器学习的文档分析服务，能够自动从扫描的文档、图像或 PDF 文件中提取文本、表格、表单数据和其他结构化信息** 。与传统的光学字符识别（OCR）技术不同，Amazon Textract 不仅能够识别文本，还能理解文档的布局和内容结构，从而提取有意义的数据。

## Amazon Lex
Amazon Lex 是 AWS 提供的 **一项对话式人工智能服务，用于构建聊天机器人和语音助手**。它支持自然语言处理（NLP）和自动语音识别（ASR），能够理解语音和文本输入，帮助开发者快速创建具备对话能力的应用程序。

## Amazon Comprehend
Amazon Comprehend 是 AWS 提供的一项 **自然语言处理（Natural Language Processing, NLP）服务**，能够从非结构化文本中提取有意义的信息。它使用机器学习技术分析文本，识别情感、关键短语、实体、语言以及文本之间的主题关系，帮助用户将非结构化数据转化为可操作的洞察。

## Amazon Personalize
Amazon Personalize 是 AWS 提供的 **一项机器学习服务，旨在帮助开发者快速构建个性化推荐系统**，无需具备深厚的机器学习技能或经验。它可以用于创建推荐、个性化搜索结果以及动态内容个性化等功能，广泛应用于电子商务、媒体流服务、在线教育等领域。

## Amazon Kendra
Amazon Kendra 是 AWS 提供的 **一项智能企业搜索服务，利用机器学习技术，帮助用户从企业内部的各种数据源中快速找到准确的答案**。它能够理解自然语言查询（NLQ，Natural Language Query），并返回相关性高的搜索结果，而不仅仅是简单的关键字匹配。

## AWS Migration Hub
AWS Migration Hub 是 AWS 提供的一项集中式服务，旨在 **帮助用户规划、跟踪和管理应用程序迁移到 AWS 云的过程** 。通过 Migration Hub，用户可以在一个统一的界面中查看迁移进度，无论是使用 AWS 原生迁移工具还是第三方迁移工具，都能集中管理和监控。

Migration Hub 的主要目标是简化迁移流程，为用户提供全面的可见性，帮助企业更高效地将本地数据中心迁移到 AWS 云。

## AWS Cloud Adoption(采用) Framework (AWS CAF)
AWS Cloud Adoption Framework (AWS CAF) 是 Amazon Web Services (AWS) **提供的一套全面的指导原则和最佳实践框架，旨在帮助组织规划、实施和优化云迁移及数字化转型**。AWS CAF 提供了一个结构化的方法，帮助企业在技术、运营和业务层面上实现高效的云计算采用，同时确保迁移过程中的安全性、合规性和成本优化。

## AWS Application Migration Service（AWS MGN）
AWS Application Migration Service（AWS MGN） 是 AWS 提供的一项迁移服务，旨在 **帮助用户将本地数据中心、虚拟机或其他云平台上的应用程序迁移到 AWS 云** 。AWS MGN 通过自动化迁移流程，简化了迁移工作，并最大限度地减少了迁移中断时间。它支持将物理服务器、虚拟服务器（如 VMware、Hyper-V）和云端服务器迁移到 AWS，同时保持应用程序在迁移前后的运行状态一致。

## AWS Application Discovery Service
AWS Application Discovery Service 通过收集有关本地服务器和数据库的使用情况和配置数据，帮助您规划向 AWS 云的迁移。

## AWS OpsWorks
AWS OpsWorks 是 AWS 提供的一项 **配置管理服务，用于帮助用户在 AWS 上自动化和管理应用程序的部署、配置和操作**。

## AWS Trusted Advisor
AWS Trusted Advisor 是 AWS 提供的一项 **实时建议服务，帮助用户优化其 AWS 环境的性能、成本、安全性、容错性和服务配额使用情况** 。它会根据 AWS 的最佳实践，自动分析用户的 AWS 资源，并提供优化建议，帮助用户更高效地使用 AWS 服务，同时降低成本并提高安全性。

### 使用案例
* 优化成本和效率：标识未使用的资源和确定降低成本的机会。评估您的 AWS 环境并采取措施持续优化效率。
* 解决安全漏洞：评估您的 AWS 环境是否符合安全标准和最佳实践。
* 提升性能：分析您的 AWS 环境的使用情况和配置，以提高应用程序的速度和响应能力。
* 提高弹性：检查您的 AWS 环境，确定是否缺少冗余和资源过度使用。
* 跟踪服务限制：检查您账户的使用情况，并在账户接近或超过服务限制时收到通知。

## Amazon Inspector(检查员)
Amazon Inspector 是 AWS 提供的一项 **自动化的安全评估服务，用于帮助客户发现 AWS 环境中的安全漏洞和配置问题** 。它能够扫描运行在 AWS 上的资源（如 EC2 实例、容器镜像等），识别潜在的漏洞、暴露的网络访问权限以及不符合安全最佳实践的配置，并提供修复建议。

在 Amazon Inspector 中，单词 "Inspector" 的意思是 检查员 或 审查员，表示这个服务的主要功能是对 AWS 环境中的资源进行 检查、审查和评估。**它的职责类似于一个安全检查员，负责扫描和发现潜在的安全漏洞或配置问题**。

## Amazon GuardDuty
Amazon GuardDuty 是一项 **威胁检测服务，来识别 AWS 环境中的可疑活动和潜在的恶意活动** 。可持续监控、分析和处理您 AWS 环境中的 AWS 数据源和日志。 GuardDuty 使用威胁情报源（例如恶意 IP 地址和域名列表、文件哈希和机器学习 (ML) 模型）来识别 AWS 环境中的可疑活动和潜在的恶意活动。

## AWS Shield
AWS Shield 是 Amazon Web Services（AWS）提供的一种 **分布式拒绝服务（DDoS）防护服务**，旨在保护用户的应用程序和资源免受 DDoS 攻击。通过 AWS Shield，用户可以在不影响应用程序性能的情况下，获得实时检测和自动防护功能。

## AWS Service Catalog
AWS Service Catalog 是一项服务，**帮助企业集中管理和部署经过批准的 IT 服务目录** 。通过 AWS Service Catalog，企业可以创建、管理和分发经过预定义的云资源集合（称为产品），这些产品可以包括虚拟机、数据库、应用程序部署模板等。它旨在帮助企业实现云资源的标准化、控制和高效部署，同时确保符合组织的治理和合规性要求。

## Amazon CloudWatch
Amazon CloudWatch 是 AWS 提供的一项 **监控和管理服务，用于收集、分析和可视化 AWS 云资源及应用程序的性能和运行数据** 。通过 CloudWatch，用户可以实时监控资源的运行状态、设置警报、自动响应事件，并优化应用程序和基础设施的性能。

## AWS CloudTrail
AWS CloudTrail 是 AWS 提供的一项 **日志记录和监控服务，用于跟踪和记录 AWS 账户中的操作事件** 。CloudTrail 会记录所有对 AWS 服务的 API 调用，包括通过 AWS 管理控制台、命令行工具、SDK 和其他服务发起的操作。通过这些记录，用户可以进行安全分析、合规性检查、资源变更审计以及问题排查。

## AWS Config
AWS Config 是一项完全托管的服务，用于 **持续评估、审核和记录 AWS 资源的配置变化** 。通过 AWS Config，用户可以跟踪 AWS 资源的配置历史，了解资源的当前状态，以及资源配置是否符合指定的合规性要求（如安全性、成本控制等）。它帮助用户实现资源的可视化管理、合规性检查和配置变更的自动化审计。

## AWS Audit(审计) Manager
AWS Audit Manager 是 Amazon Web Services（AWS）提供的一种自动化审计准备服务，旨在帮助用户简化和加速合规性评估流程。该服务通过自动收集和整理 AWS 服务使用情况的数据，生成与行业标准和法规（如 GDPR、HIPAA、ISO 27001 等）相关的审计证据，使用户能够更高效地管理合规性工作。**持续审计您的 AWS 使用情况，以简化风险与合规性的评估。**

## [AWS Well-Architected Framework](./Well-ArchitectedFramework.md)
AWS Well-Architected Framework 是由 AWS 提供的 **一套云架构最佳实践指导原则，旨在帮助用户设计、构建和优化其在 AWS 云上的工作负载** 。通过 Well-Architected Framework，用户可以评估其架构的质量，识别潜在的改进点，并确保其架构能够满足业务需求，同时遵循高效、安全、可靠和经济的云架构设计原则。

## AWS Support
AWS Support 是 Amazon Web Services 提供的 **一套支持服务，旨在帮助客户更好地使用 AWS 平台，解决技术问题，优化云架构，并确保工作负载的高效运行** 。AWS Support 服务涵盖从基础技术支持到高级架构建议的广泛范围，适用于各种规模的企业和不同的技术需求。

## AWS Systems Manager（SSM）
AWS Systems Manager（SSM） 是一个集成的管理工具，能够帮助您在 AWS 云环境和本地数据中心中集中管理基础设施资源。它 **提供了一套工具，用于自动化操作任务、监控系统状态、管理配置和应用补丁，从而提高操作效率、安全性和可见性** 。

## Amazon EC2 Session Manager
Amazon EC2 Session Manager 是 AWS Systems Manager 的一项功能，**提供了一种安全、无代理（Agentless）且无需打开端口的方式，用于直接管理 Amazon EC2 实例或本地服务器**。它允许用户通过 AWS 管理控制台、AWS CLI 或 AWS SDK 在浏览器或终端中直接访问实例，无需使用传统的 SSH 或 RDP 工具。

## EC2 Instance Connect
EC2 Instance Connect 是 AWS 提供的一种服务，**允许您通过 AWS 管理控制台或命令行界面（CLI）直接连接到 Amazon EC2 实例，无需使用传统的 SSH 客户端或管理密钥对**。它简化了实例访问流程，并增强了安全性。

## AWS Professional Services
AWS Professional Services 是 AWS 提供的一项 **专业咨询服务，旨在帮助客户加速云采用、优化云使用，并实现业务目标** 。通过与客户的 IT 团队、开发团队以及合作伙伴协作，AWS Professional Services 提供技术指导、最佳实践和定制化的解决方案，帮助企业在 AWS 云上成功实施复杂的项目，包括迁移、现代化、创新和运营优化。

AWS Professional Services 结合 AWS 的技术能力和深厚的行业经验，为客户提供从战略规划到执行落地的全方位支持，确保客户能够最大化地利用 AWS 云的优势。

# 计算
## AWS Batch
AWS Batch 是一项完全托管的 **批处理计算服务**，专门用于运行大规模的批处理任务。它可以帮助用户轻松、高效地运行数千甚至数百万个批处理任务，而无需管理底层的计算基础设施。AWS Batch 会根据任务的需求动态地配置计算资源（如 Amazon EC2 实例或 AWS Fargate），并优化资源的分配以降低成本。

## AWS Elastic Beanstalk
AWS Elastic Beanstalk 是一项由 Amazon Web Services (AWS) 提供的 **全托管平台即服务（PaaS），用于快速部署和管理应用程序** 。它支持多种开发语言和框架，允许开发者专注于代码，而无需担心底层基础设施的配置、管理和扩展。

## Amazon Lightsail
Amazon Lightsail 是 AWS **提供的一种易于使用、经济实惠的云平台服务** ，专为那些需要简单云解决方案的用户设计。它提供了预配置的虚拟服务器（实例）、存储、数据库、网络和管理工具，使用户可以快速启动和运行小型应用程序、网站和开发环境，而无需深入了解复杂的云基础设施。

## AWS Outposts
AWS Outposts 是 Amazon Web Services 提供的一项 **混合云解决方案，允许企业将 AWS 的基础设施、服务和工具扩展到本地数据中心或边缘位置**。通过 Outposts，用户可以在自己的本地环境中运行与 AWS 云中一致的服务、API 和工具，从而实现低延迟、本地数据处理和混合部署的需求。

## AWS Local Zones
AWS Local Zones 是 Amazon Web Services（AWS）提供的 **一种基础设施部署选项，旨在将计算、存储、数据库和其他 AWS 服务扩展到距离用户更近的地理位置**。通过 AWS Local Zones，用户可以在靠近最终用户或特定位置的地方运行延迟敏感的应用程序，从而实现低延迟和更高性能。

## AWS Wavelength(波长)
AWS Wavelength 是 Amazon Web Services（AWS）推出的一种专为超低延迟应用程序设计的服务，旨在将 AWS 的计算和存储服务嵌入到电信运营商的 5G 网络边缘。通过 AWS Wavelength，开发者可以在距离最终用户更近的地方运行延迟敏感的工作负载，充分利用 5G 网络的低延迟、高带宽和广泛覆盖的特性。

### AWS Wavelength 与 AWS Local Zones 的区别

| 特性         | **AWS Wavelength Zones**                 | **AWS Local Zones**                          |
| ------------ | ---------------------------------------- | -------------------------------------------- |
| **部署位置** | 嵌入到电信运营商的 5G 网络边缘。         | 部署在 AWS 定义的特定地理位置。              |
| **延迟**     | 提供超低延迟（几毫秒），适用于实时应用。 | 提供低延迟，但通常高于 Wavelength。          |
| **适用场景** | 需要 5G 网络支持的超低延迟应用。         | 需要靠近用户的低延迟应用，但不依赖 5G 网络。 |
| **目标用户** | 5G 网络用户和延迟敏感型应用开发者。      | 需要靠近最终用户或特定地理位置的企业。       |

## Amazon EC2 Auto Scaling
Amazon EC2 Auto Scaling 是 AWS 提供的一项服务，用于 **根据应用程序的需求动态地调整 Amazon EC2 实例的数量** 。它能够自动扩展或缩减 EC2 实例，以确保应用程序在负载增加时拥有足够的计算资源，同时在负载减少时节省成本。

## AWS Certificate Manager
AWS Certificate Manager (ACM) 是 AWS 提供的一项托管服务，**用于轻松管理 SSL/TLS 证书，帮助用户保护其网站、应用程序及其他资源的通信安全**。通过 ACM，用户可以快速申请、部署和管理证书，无需手动完成复杂的证书生成、续订和部署流程。

## AWS Secrets Manager
AWS Secrets Manager 是一项由 AWS 提供的托管服务，**用于安全地存储、管理和检索敏感信息（称为“密钥”或“秘密”）**，例如数据库凭据、API 密钥、密码和其他配置数据。它能够帮助开发者和企业避免将敏感信息硬编码到应用程序中，同时提供自动轮换、访问控制和审计功能，以提高安全性和合规性。

## AWS Key Management Service
AWS Key Management Service (AWS KMS) 是一项 **托管的加密密钥管理服务** ，用于创建和管理加密密钥，并控制其在各种 AWS 服务和应用程序中的使用。AWS KMS 提供了一个安全且高度可用的环境，用于生成、存储和保护密钥，同时支持对数据进行加密和解密操作。

## AWS CloudHSM
AWS CloudHSM 是 **一种基于云的硬件安全模块（HSM）服务，允许用户在 AWS 云中安全地生成和管理加密密钥**。CloudHSM 提供专用的硬件设备，帮助用户满足严格的安全性、合规性和数据主权要求，同时具备高性能和低延迟。

| 特性                | **AWS KMS**                      | **AWS Secrets Manager**                  |
| ------------------- | -------------------------------- | ---------------------------------------- |
| **主要用途**        | 管理加密密钥，用于数据加密和解密 | 管理敏感信息（如密码、API 密钥）         |
| **自动轮换**        | 支持（密钥轮换每年一次）         | 支持（可自定义轮换周期和逻辑）           |
| **加密支持**        | 专注于密钥管理和加密操作         | 不直接加密数据，而是存储加密后的敏感信息 |
| **与 AWS 服务集成** | 深度集成（S3、EBS、RDS 等）      | 集成有限，主要用于检索敏感信息           |
| **审计和监控**      | 支持（通过 CloudTrail）          | 支持（通过 CloudTrail）                  |
| **成本**            | 按密钥数量和 API 调用计费        | 按存储的密钥数量和 API 调用计费          |

| 特性           | AWS CloudHSM                     | AWS KMS                          |
| -------------- | -------------------------------- | -------------------------------- |
| **密钥控制权** | 用户完全控制密钥，AWS 无法访问   | AWS 管理密钥，但用户可以定义权限 |
| **硬件安全性** | 使用专用 HSM 设备                | 使用共享 HSM 设备                |
| **性能**       | 高性能，适合高吞吐量需求         | 性能适中，适合大多数通用场景     |
| **合规性**     | 符合 FIPS 140-2 Level 3          | 符合 FIPS 140-2 Level 2          |
| **管理复杂性** | 用户需自行管理密钥和 HSM         | AWS 负责大部分密钥管理工作       |
| **成本**       | 较高，适合对安全性要求极高的场景 | 较低，适合一般场景               |


## Amazon Rekognition
Amazon Rekognition 是 AWS 提供的一项 **基于机器学习的图像和视频分析服务** 。它能够帮助开发者轻松地从图像和视频中提取信息，例如对象检测、人脸识别、行为分析等。开发者无需具备机器学习经验，只需通过 API 就可以快速集成这些功能，用于各种应用场景，如安全监控、内容审核、用户身份验证等。

## Amazon SageMaker
Amazon SageMaker 是 AWS 提供的一项完全托管的 **机器学习服务，旨在帮助开发者和数据科学家快速构建、训练和部署机器学习（ML）模型** 。它覆盖了机器学习工作流的整个生命周期，从数据准备到模型训练、优化和部署，用户无需管理底层的基础设施。

## AWS Artifact
AWS Artifact 是 AWS 提供的一项自助式门户服务，专注于 **为用户提供与合规性和安全性相关的文档和报告** 。它是 AWS 合规性框架的一部分，帮助用户获取 AWS 的审计报告、认证和协议，以满足其自身的合规性需求。

## Amazon API Gateway
Amazon API Gateway 是 AWS 提供的一项完全托管的服务，**用于创建、发布、维护、监控和保护 API（应用程序编程接口）**。

## AWS Storage Gateway
AWS Storage Gateway 是一项 **混合云存储服务，旨在帮助企业将本地环境与 AWS 云存储无缝集成**。通过 Storage Gateway，用户可以将本地数据存储扩展到 AWS 云中，同时继续以现有的方式访问和管理数据。这项服务适用于数据备份、归档、灾难恢复以及本地到云的存储扩展。

## AWS Personal Health Dashboard (PHD) 
AWS Personal Health Dashboard (PHD) 是 AWS 提供的一项服务，旨在 **为用户提供与其 AWS 资源相关的个性化运行状况信息和通知**。与 AWS 服务的整体运行状况页面（Service Health Dashboard）不同，Personal Health Dashboard 专注于用户账户下的具体资源，提供与用户资源直接相关的实时事件更新、潜在问题通知以及缓解建议。

## AWS Service Health Dashboard (SHD)
AWS Service Health Dashboard (SHD) 是 AWS 提供的一个公开可访问的工具，用于 **显示所有 AWS 服务和区域的整体运行状况信息**。它提供了 AWS 服务的实时状态更新，包括服务中断、性能问题、计划维护等事件，帮助用户了解 AWS 平台的运行情况以及是否存在可能影响其应用程序的问题。

| **功能**     | **AWS Personal Health Dashboard**  | **AWS Service Health Dashboard**              |
| ------------ | ---------------------------------- | --------------------------------------------- |
| **关注点**   | 用户账户下的资源和服务运行状况     | AWS 全球服务的整体运行状况                    |
| **个性化**   | 提供与用户资源相关的个性化通知     | 不提供个性化信息，显示所有 AWS 服务的运行状况 |
| **实时性**   | 提供实时更新和缓解建议             | 通常有一定的延迟                              |
| **事件范围** | 仅限于用户账户下的资源和服务       | 针对所有 AWS 用户的公共事件                   |
| **适用场景** | 了解与用户资源相关的事件并采取行动 | 查看 AWS 服务的整体运行状况                   |

## Amazon Lumberyard
Amazon Lumberyard 是由 AWS 开发并免费提供的 **一款跨平台 3D 游戏引擎**。

## Amazon CloudSearch
Amazon CloudSearch 是 AWS 提供的一项 **全托管搜索服务**，允许用户轻松地为其网站或应用程序集成强大的搜索功能。

## AWS WAF
AWS WAF（Web Application Firewall，Web 应用防火墙）是 AWS 提供的一项托管服务，**用于保护 Web 应用程序或 API 免受常见的 Web 威胁，例如 SQL 注入、跨站脚本（XSS）攻击以及分布式拒绝服务（DDoS）攻击等**。AWS WAF 帮助用户在不影响应用程序性能的情况下，提高应用程序的安全性和可用性。

## Amazon Cognito
Amazon Cognito 是 AWS 提供的一项 **身份验证和用户管理服务，专为 Web 和移动应用程序设计** 。它帮助开发者快速、安全地添加用户注册、登录、访问控制以及身份验证功能，而无需自行开发复杂的身份管理系统。

# 终端用户计算
## Amazon AppStream 2.0
Amazon AppStream 2.0 是 **一项完全托管的 AWS End User Computing（EUC）服务，旨在流式传输软件即服务（SaaS）应用程序，并将桌面应用程序转换为 SaaS，而无需重写代码或重构应用程序**。使用 AppStream 2.0，您可以快速将应用程序扩展到全球各地的用户，而无需管理任何基础架构。 AppStream 2.0 提供多会话功能，允许您在单个 AppStream 2.0 实例上预置多个用户会话。这使您能够优化资源利用率，并且有助于降低成本，在不进行过度预置的情况下支持多种用户类型。

## AWS WorkSpaces
AWS WorkSpaces 是 Amazon 提供的一种完全托管的**桌面即服务（DaaS）**解决方案。它允许用户在云中创建虚拟桌面环境，提供安全、高性能且可扩展的桌面体验。通过 AWS WorkSpaces，用户可以在任意设备上访问个性化的虚拟桌面，而无需管理底层硬件或复杂的虚拟桌面基础设施。

### AWS WorkSpaces 与 Amazon AppStream 2.0 的区别
| **特性**     | **AWS WorkSpaces**                                                         | **Amazon AppStream 2.0**                                                                       |
| ------------ | -------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| **服务类型** | 桌面即服务（DaaS）。提供完整的虚拟桌面环境。                               | 应用流服务。将单个应用程序流式传输到用户设备，而不是完整的桌面环境。                           |
| **主要用途** | 为用户提供完整的虚拟桌面，适用于日常办公、远程工作或开发环境。             | 为用户提供特定的应用程序访问，适用于需要运行单个或一组应用程序的场景，例如设计工具或企业软件。 |
| **使用场景** | - 远程办公、BYOD（自带设备）。<br>- 开发测试环境。<br>- 企业桌面替代方案。 | - 应用程序流式传输（如 CAD、3D 渲染、财务应用）。<br>- 教育和培训。<br>- SaaS 应用交付。       |


## Amazon WorkSpaces Web
Amazon WorkSpaces Web 是 Amazon Web Services (AWS) 提供的一项完全托管的服务，旨在 **为用户提供安全、低延迟的基于浏览器的访问方式，用于访问内部企业系统、SaaS 应用程序和敏感数据，而无需将数据直接暴露到用户设备上**。它通过虚拟化的浏览器会话，保护企业资源的安全，同时提升用户体验。

### Amazon WorkSpaces 与 Amazon WorkSpaces Web 的区别
| 特性               | **Amazon WorkSpaces**                                | **Amazon WorkSpaces Web**                          |
| ------------------ | ---------------------------------------------------- | -------------------------------------------------- |
| **使用场景**       | 提供完整的虚拟桌面环境，适合需要访问多种应用的用户。 | 提供安全的浏览器访问，适合仅需访问网页资源的用户。 |
| **数据存储**       | 用户数据存储在虚拟桌面上。                           | 数据从不离开 AWS 云，用户设备上无数据存储。        |
| **复杂性**         | 需要更多的配置和管理。                               | 完全托管，简单易用。                               |
| **成本**           | 成本较高，按虚拟桌面资源收费。                       | 成本较低，按浏览器会话收费。                       |
| **支持的应用类型** | 支持桌面应用程序和浏览器访问。                       | 仅支持基于浏览器的应用程序访问。                   |
| **设备要求**       | 需要安装 WorkSpaces 客户端。                         | 无需安装客户端，通过现代浏览器即可访问。           |
| **适用场景**       | 适合需要完整桌面体验的用户，例如开发者或设计师。     | 适合需要访问 SaaS 应用或企业内部网页的用户。       |
| **管理复杂度**     | 需要管理虚拟桌面实例和存储。                         | AWS 完全托管，无需管理底层基础设施。               |
| **安全性**         | 数据可以存储在虚拟桌面上，需额外保护。               | 数据从不离开 AWS 云，天然更安全。                  |
| **资源使用**       | 占用更多计算和存储资源。                             | 占用较少资源，仅运行云端浏览器会话。               |


## AWS Cost and Usage Report
AWS Cost and Usage Report (CUR) 是 AWS 提供的一项服务，用于生成详细的成本和使用情况报告，帮助用户深入了解其 AWS 服务的使用情况和费用明细。CUR 是 AWS 提供的最全面、最详细的计费数据来源，能够追踪每个 AWS 服务、每个账户、每个资源的使用情况和费用。

## AWS Directory Service
AWS Directory Service 是 AWS 提供的一项托管服务，用于 **在云中设置和管理目录服务**。它允许用户将其现有的 Microsoft Active Directory (AD) 或其他目录服务扩展到 AWS 云中，或者直接在 AWS 中创建新的目录。AWS Directory Service 使企业能够轻松管理用户身份、认证、设备、组策略以及资源访问权限，同时减少了管理目录基础设施的复杂性。

## Amazon Pinpoint
Amazon Pinpoint 是 AWS 提供的一项灵活的、**多渠道营销和用户参与服务**，主要用于帮助企业与客户进行高效的沟通和互动。它允许用户通过多种渠道（如电子邮件、短信、推送通知、语音消息和社交媒体）向客户发送个性化的消息，同时提供详细的分析功能，用于监控和优化营销活动的效果。

# 容器
## Amazon Elastic Container Registry
Amazon Elastic Container Registry (Amazon ECR) 是 Amazon Web Services (AWS) 提供的 **一项全托管的容器镜像存储服务，专为存储、管理和部署容器镜像而设计**。它与 Amazon ECS（Elastic Container Service）、Amazon EKS（Elastic Kubernetes Service）以及 Docker 等容器工具无缝集成，帮助开发者轻松管理容器化应用的镜像。

## Amazon Elastic Container Service (ECS)
Amazon Elastic Container Service (ECS) 是 Amazon Web Services (AWS) 提供的一项 **高性能、可扩展的容器管理服务，支持运行、停止和管理 Docker 容器化的应用程序**。ECS 消除了用户部署和管理容器编排软件的复杂性，能够让开发者专注于构建和运行容器化应用程序。

## Amazon Elastic Kubernetes Service (EKS)
Amazon Elastic Kubernetes Service (EKS) 是 Amazon Web Services (AWS) 提供的一项 **完全托管的 Kubernetes 服务，旨在帮助用户轻松部署、运行和扩展基于 Kubernetes 的容器化应用程序**。EKS 让用户无需自己安装、操作或维护 Kubernetes 控制平面，提供高可用性、安全性和自动化功能，使其成为运行容器化工作负载的理想选择。

## AWS Fargate
AWS Fargate 是 AWS 提供的一种 **无服务器容器运行服务，允许用户无需管理底层服务器或集群即可运行容器化应用程序** 。它与 Amazon ECS（Elastic Container Service） 和 Amazon EKS（Elastic Kubernetes Service） 集成，用户只需定义容器的资源需求和配置，Fargate 会自动处理容器的计算资源分配、启动和扩展。

# 分析服务
## Amazon Athena
Amazon Athena 是 AWS 提供的一项 **交互式查询服务，用于直接在 Amazon S3 上运行 SQL 查询，无需加载或移动数据** 。它是一种 无服务器（Serverless） 的服务，用户无需管理基础设施，只需提供 SQL 查询，Athena 会自动处理底层的计算资源，返回查询结果。

## Amazon Kinesis
Amazon Kinesis 是 AWS 提供的一套完全托管的 **实时数据流处理服务，旨在帮助开发者轻松收集、处理和分析大规模实时数据流** 。它能够以毫秒级的延迟处理来自数百万个数据源（如 IoT 设备、日志文件、应用程序、点击流等）的数据，使用户能够实时获取洞察并采取行动。

## Amazon Redshift
Amazon Redshift 是亚马逊云服务（AWS）推出的一种 **完全托管的云端数据仓库服务，专为大规模数据存储和分析而设计**。它能够高效地处理 PB 级别的数据，支持复杂的查询和分析操作，帮助企业快速从海量数据中获取洞察。

## AWS Data Exchange(交换)
AWS Data Exchange 是 Amazon Web Services (AWS) 提供的一项 **数据共享服务，旨在让用户轻松查找、订阅和使用第三方数据集**。通过 AWS Data Exchange，用户可以访问来自各种数据提供商的高质量数据，用于分析、机器学习和业务决策，同时数据提供商也可以通过该平台安全地分发其数据产品。

## Amazon EMR
Amazon EMR（Elastic MapReduce） 是 AWS 提供的一项托管服务，用于 **处理和分析大规模数据**。它基于流行的大数据框架（如 Apache Hadoop、Apache Spark、Presto 等），帮助用户快速、经济高效地运行分布式计算任务。Amazon EMR 可用于处理各种类型的数据，包括日志数据、事务数据、点击流数据、传感器数据等，适用于数据分析、机器学习、实时流处理和大数据应用开发。

## AWS Glue(胶水)
AWS Glue 是一项由 AWS 提供的无服务器（Serverless）数据集成服务，**专门用于简化数据的发现、准备、转换和加载（ETL：Extract, Transform, Load）流程** 。它可以帮助用户轻松地将数据从多个来源提取、清洗和转换后加载到目标数据存储中（如数据湖或数据仓库），以便进行分析和查询。

## Amazon Managed Streaming for Apache Kafka
Amazon Managed Streaming for Apache Kafka (Amazon MSK) 是一项由 AWS 提供的全托管服务，专门用于运行和管理 Apache Kafka。Apache Kafka 是一种广泛使用的开源 **分布式事件流平台，用于构建实时数据流应用程序和数据管道**。Amazon MSK 让用户无需担心 Kafka 集群的设置、维护和扩展，专注于开发和运行应用程序。

## Amazon OpenSearch Service
Amazon OpenSearch Service（原名 Amazon Elasticsearch Service）是 AWS 提供的一项全托管服务，用于部署、操作和扩展 OpenSearch 和 Elasticsearch 集群。这项服务 **支持用户在 AWS 云中执行实时的日志分析、全文搜索、监控和可视化等任务**，无需管理底层的基础设施。

## Amazon QuickSight
Amazon QuickSight 是 AWS 提供的一项基于云的 **商业智能（BI）服务，旨在帮助用户快速创建可视化报表、分析数据并从数据中提取洞察** 。它支持从各种数据源（如 AWS 数据服务、第三方数据库、本地文件等）导入数据，通过直观的仪表板和交互式图表，帮助用户轻松实现数据分析和共享。

## Amazon Forecast
Amazon Forecast 是 AWS 提供的一项 **机器学习驱动的时间序列预测服务，用于帮助用户生成高精度的业务预测**。它利用 机器学习（ML）技术，结合历史数据和相关变量（如促销活动、天气条件等），生成针对特定用例的预测结果。

## AWS Service Quotas
Service Quotas 是 AWS 提供的一项服务，**用于管理和查看 AWS 服务的配额（也称为限制）**。每个 AWS 服务都有其默认的资源或操作限制，例如 API 调用次数、实例数量、存储容量等。通过 Service Quotas，用户可以方便地查看这些限制，并根据需要向 AWS 提交配额增加请求。

# 前端 Web和移动
## AWS Amplify(放大、增强)
AWS Amplify 是 Amazon Web Services 提供的一套工具和服务，专门用于帮助开发人员 **快速构建、部署和管理全栈 Web 和移动应用程序**。它简化了前端和后端的开发流程，提供了强大的工具链和托管服务，支持从前端框架到云后端的无缝集成。

## AWS AppSync
AWS AppSync 是 Amazon Web Services 提供的一项 **全托管的 GraphQL API 服务，用于构建现代化的应用程序，支持实时数据查询、变更和订阅**。它允许开发者通过一个单一的 GraphQL 接口访问和管理来自多个数据源的数据（如 Amazon DynamoDB、RDS、Lambda、HTTP API 等），从而简化数据访问和整合。

## AWS Device Farm(农场)
AWS Device Farm 是 Amazon Web Services (AWS) 提供的 **一项应用测试服务，旨在帮助开发者在真实设备上测试其移动应用程序和网页应用程序**。通过 AWS Device Farm，开发者可以在云端访问各种真实设备（包括智能手机、平板电脑等），以便快速发现问题并优化用户体验，而无需构建和维护自己的测试基础设施。

# 物联网 (IoT)
## AWS IoT Greengrass
AWS IoT Greengrass 是一项 **边缘计算服务，旨在将云计算的功能扩展到本地设备，使物联网（IoT）设备能够在边缘环境中运行 AWS Lambda 函数、与其他设备通信、处理数据、执行机器学习推理，并与 AWS 云服务无缝集成**。

## AWS IoT Core
AWS IoT Core 是 AWS 提供的一种托管服务，专门 **用于连接物联网（IoT）设备到云端，并实现设备之间、设备与云端的安全通信和交互**。它为开发者提供了一个强大的平台，用于构建、管理和扩展物联网应用，而无需管理底层基础设施。

## Amazon Detective
Amazon Detective 是亚马逊云服务（AWS）提供的 **一项安全分析服务，旨在帮助用户调查和分析潜在的安全问题或可疑活动**。通过自动化的数据收集和图形分析，Amazon Detective 可以快速识别、理解和解决安全事件的根本原因。

## AWS Security Hub(中心)
AWS Security Hub 是 Amazon Web Services 提供的一项 **全托管安全服务，旨在集中管理和分析来自多个 AWS 服务和第三方安全工具的安全警报和合规性状态**。它为用户提供统一的安全视图，帮助识别潜在的安全问题，简化合规性检查，并增强整体安全态势。

## AWS Compute Optimizer
AWS Compute Optimizer 是 **一项基于机器学习的服务，旨在帮助用户优化 AWS 资源的使用，降低成本并提高性能**。它会分析用户的工作负载数据，并根据实际使用情况提供优化建议，帮助用户选择最适合的 Amazon EC2 实例、Amazon EBS 卷、Amazon Lambda 函数 和 Amazon ECS 任务 配置。

## AWS Resource Access Manager
AWS Resource Access Manager (RAM) 是一项 AWS 服务，用于 **帮助用户在多个 AWS 账户或 AWS 组织中的账户之间安全地共享 AWS 资源**。通过 RAM，用户可以避免为每个账户重复创建资源，从而简化管理并优化成本。

## Amazon CodeGuru
Amazon CodeGuru 是一项基于机器学习的开发者工具，旨在帮助开发人员提高代码质量并优化应用程序性能。它通过分析代码和运行时行为，提供代码审查建议和性能优化建议，从而减少代码中的漏洞、提高应用程序效率并降低运行成本。

Amazon CodeGuru 包括两个主要组件：

1. CodeGuru Reviewer：用于自动化代码审查，检测代码中的潜在问题并提供改进建议。
2. CodeGuru Profiler：用于分析应用程序运行时性能，识别性能瓶颈并提供优化建议。

## AWS Identity and Access Management
AWS Identity and Access Management（IAM） 是 AWS 提供的一项核心服务，用于安全地管理对 AWS 资源的访问权限。IAM 允许用户控制谁（身份）可以访问哪些 AWS 资源，以及可以执行哪些操作，从而帮助企业实现细粒度的访问控制和增强安全性。

## AWS IAM Identity Center
AWS IAM Identity Center（原 AWS Single Sign-On, SSO） 是一项 **集中式身份管理服务，用于帮助用户轻松管理对多个 AWS 账户和业务应用程序的访问**。通过 IAM Identity Center，用户可以使用单一的登录凭据访问 AWS 账户、AWS 服务以及支持 SAML 2.0 的第三方应用程序。

| **服务** | **AWS Identity and Access Management (IAM)**                                              | **AWS IAM Identity Center**                                                                                            |
| -------- | ----------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **定义** | AWS IAM 是一种核心服务，用于管理 AWS 资源的访问权限，提供用户、组、角色和策略的管理功能。 | AWS IAM Identity Center 是一个集中化的身份管理服务，用于跨多个 AWS 账户和第三方应用程序实现单点登录（SSO）和权限管理。 |
| **用途** | 管理对单个 AWS 账户中资源的访问权限，提供细粒度的权限控制。                               | 集中管理多个 AWS 账户和支持 SAML 2.0 的第三方应用的用户访问权限，简化跨账户和应用的访问管理。                          |

## Reserved Instances (RIs)
对于有些服务，如 Amazon EC2 和 Amazon RDS，您可以购买预留容量。与使用等量按需容量相比，使用预留实例可节省高达 75% 的费用。预留实例有 3 个付款选项 – 全额预付 (AURI)、部分预付 (PURI) 或无预付 (NURI)。

购买预留实例时，预付金额越高，享受的折扣就越大。要最大程度地节省资金，您可以预付全部费用，从而享受最大折扣。部分预付预留实例所提供的折扣较低，但相应的预付费用也较低。最后，您可以选择不预付任何费用，但享受的折扣较小，不过这种模式可让您留出资金来开展其他项目。

通过使用预留容量，您的组织可以最大程度地降低风险、更有预见性地管理预算并遵守需要长期执行的政策。

## AWS Global Accelerator(加速器)
AWS Global Accelerator 是一项 **网络服务，旨在通过优化全球用户访问 AWS 应用程序的路径，提高应用程序的性能和可用性**。它利用 AWS 全球基础设施（包括 AWS 的边缘网络）为用户提供低延迟、高可用性的网络访问体验。

## Amazon CloudFront(云前面)
Amazon CloudFront 是 Amazon Web Services（AWS）提供的 **内容分发网络（CDN）服务**，旨在帮助用户快速、安全地将内容（如网页、视频、图像和 API 数据）分发给全球用户。通过将内容缓存到靠近用户的边缘位置，CloudFront 提供低延迟、高吞吐量和高可用性的内容交付体验，同时内置了安全功能来保护内容和应用程序。

## Amazon Relational Database Service (RDS)
Amazon Relational Database Service (RDS) 是 Amazon Web Services (AWS) 提供的一项 **完全托管的关系型数据库服务**，旨在帮助用户轻松设置、操作和扩展关系型数据库。通过自动化的数据库管理任务（如硬件配置、数据库设置、补丁管理和备份），RDS 大幅简化了数据库的运维工作，让用户可以专注于应用程序开发。

# 数据库
## Amazon Aurora
Amazon Aurora 是 AWS 提供的 **一种高性能、企业级的关系型数据库服务，与 MySQL 和 PostgreSQL 兼容**。Aurora 结合了传统商业数据库的性能和可用性，同时具备开源数据库的简单性和经济性。它专为云环境设计，提供高吞吐量、低延迟、高可用性和自动扩展功能。

## Amazon DynamoDB
Amazon DynamoDB 是 Amazon Web Services (AWS) 提供的一项 **完全托管的 NoSQL 数据库服务**，专为需要低延迟、高吞吐量和高可用性的应用程序设计。DynamoDB 支持键值存储和文档存储，能够轻松处理任意规模的工作负载，适合多种实时、高性能场景。

## Amazon Neptune
Amazon Neptune 是 AWS 提供的一种完全托管的 **图数据库服务，专为构建和运行基于图形的应用程序而设计** 。它支持两种主流的图查询语言：Apache TinkerPop Gremlin（用于属性图）和 W3C SPARQL（用于 RDF 图），使开发者能够高效地存储和查询复杂的关系数据。

## AWS Database Migration Service
AWS Database Migration Service (DMS) 是 Amazon Web Services (AWS) 提供的一项 **完全托管的数据库迁移服务**，旨在帮助用户快速、安全地将数据库从本地或云环境迁移到 AWS。DMS 支持多种数据库引擎之间的迁移，包括关系型数据库、NoSQL 数据库和数据仓库，同时支持同构和异构数据库迁移。

## AWS Schema Conversion(转换) Tool
AWS Schema Conversion Tool (SCT) 是 Amazon Web Services (AWS) 提供的一款 **数据库架构转换工具**，旨在帮助用户将现有的数据库架构从一种数据库引擎迁移到另一种数据库引擎。它特别适用于异构数据库迁移，例如从商业数据库（如 Oracle、SQL Server）迁移到开源数据库（如 Amazon Aurora、PostgreSQL 或 MySQL）。

## Amazon WorkDocs
Amazon WorkDocs 是 AWS 提供的一种 **安全、完全托管的企业内容管理和协作服务**。它允许用户在云端存储、共享和协作处理文档、电子表格、演示文稿以及其他文件。WorkDocs 提供了类似于传统文件共享和协作工具的功能，但具备更高的安全性、可扩展性和与 AWS 服务的深度集成。

## Amazon WorkMail
Amazon WorkMail 是 AWS 提供的一种 **安全、托管的企业电子邮件和日历服务，旨在帮助企业用户轻松管理电子邮件、日历和联系人**。它支持与现有企业目录（如 Microsoft Active Directory）集成，并提供对企业级安全性和隐私的全面支持。用户可以通过常用的电子邮件客户端（如 Microsoft Outlook）或任何支持 IMAP 协议的客户端访问 WorkMail，同时也支持移动设备和 Web 浏览器。

## AWS DataSync
AWS DataSync 是一种托管的 **数据迁移服务，用于在本地存储、边缘设备和 AWS 存储服务之间自动化、快速、安全地传输数据**。它支持将数据迁移到 AWS 云中，或者在不同的 AWS 存储服务之间进行数据同步，例如 Amazon S3、Amazon EFS（Elastic File System）和 Amazon FSx。

## Amazon S3 Transfer Acceleration(加速度)
Amazon S3 Transfer Acceleration 是 AWS 提供的一项服务，旨在 **通过优化的全球网络基础设施，加速用户上传到 Amazon S3 存储桶的数据传输速度**。它利用 AWS 全球边缘网络（Amazon CloudFront 的边缘位置） 来缩短传输路径，从而显著提高远距离、大文件上传的速度。

## Amazon Elastic File System
Amazon Elastic File System（Amazon EFS） 是 AWS 提供的一种 **完全托管的弹性网络文件系统，专为支持多个 AWS 云服务和本地资源的共享文件存储而设计**。EFS 提供简单、可扩展、高可用性和持久性的文件存储解决方案，能够自动扩展和收缩以适应工作负载的变化，从而无需预置存储容量。

## Amazon FSx for Windows File Server
Amazon FSx for Windows File Server 是 AWS 提供的一种 **完全托管的文件存储服务，专为运行 Windows 应用程序的企业设计**。它支持 Windows 原生的 SMB（Server Message Block）协议 和 NTFS（New Technology File System）文件系统，为用户提供熟悉的 Windows 文件存储体验，同时具备高性能、可扩展性和与 AWS 生态系统的深度集成。

## Amazon FSx for Lustre
Amazon FSx for Lustre 是 AWS 提供的一种 **完全托管的高性能文件存储服务，专为需要快速处理大规模数据集的计算密集型工作负载而设计**。它基于开源的 Lustre 文件系统，Lustre 是一种广泛用于高性能计算（HPC）和机器学习等领域的分布式文件系统，以其超低延迟、高吞吐量和高并发性能而闻名。

## Amazon Elastic Block Store
Amazon Elastic Block Store (Amazon EBS) 是 AWS 提供的一种 **高性能块存储服务，专为与 Amazon EC2 实例配合使用而设计**。EBS 提供低延迟、持久性、高可用性和可扩展性的存储解决方案，适用于各种工作负载，包括数据库、文件系统、容器化应用和分析等。

## Amazon WorkSpaces
Amazon WorkSpaces 是 AWS 提供的一项**托管桌面即服务（DaaS，Desktop as a Service）**解决方案，允许用户在云中创建、管理和访问虚拟桌面。通过 WorkSpaces，用户可以从任何设备（如 PC、Mac、平板电脑或智能手机）安全地访问其虚拟桌面，并获得与传统物理桌面类似的使用体验。

## AWS Professional Services
AWS Professional Services 是 AWS 提供的一项 **专业咨询服务，旨在帮助企业客户加速其云迁移、部署和优化过程**。该服务由 AWS 的专业团队提供支持，这些专家与客户的 IT 团队、合作伙伴及其他利益相关方协作，帮助客户设计、开发和实施基于 AWS 云的解决方案，以满足其独特的业务需求。

## AWS Concierge Support Team
是 AWS 针对企业支持（Enterprise Support）客户提供的一项专属支持服务。该团队由经验丰富的 AWS 专家组成，专注于为客户提供与账单和账户管理相关的高级支持。

## AWS Well-Architected Tool
AWS Well-Architected Tool 是 Amazon Web Services（AWS）提供的 **一种云架构评估和优化工具**，帮助用户根据 AWS Well-Architected Framework 的最佳实践，评估其工作负载的架构设计，并识别潜在的改进机会。该工具旨在确保用户的云架构能够实现高效、安全、可靠和经济的目标。

## AWS Backup
AWS Backup 是 Amazon Web Services (AWS) 提供的一项 **集中式、完全托管的备份服务，旨在帮助用户简化和自动化 AWS 资源的备份和恢复操作**。通过 AWS Backup，用户可以轻松地为各种 AWS 服务（如 EC2、RDS、EFS 等）创建备份策略，集中管理备份任务，并确保数据的安全性和合规性。

# 应用程序集成
## Amazon EventBridge
Amazon EventBridge 是 Amazon Web Services (AWS) 提供的 **一种无服务器事件总线服务，用于实现应用程序之间的事件驱动架构**。它可以从 AWS 服务、自定义应用程序或第三方 SaaS 应用程序中捕获事件，并将这些事件路由到目标服务，从而实现实时的事件处理和自动化工作流。

EventBridge 的核心功能是事件路由和事件驱动架构的构建，用户可以基于事件模式定义规则，自动触发目标操作。

## Amazon Simple Notification(通知) Service
Amazon Simple Notification Service (Amazon SNS) 是 Amazon Web Services (AWS) 提供的一项 **完全托管的消息发布/订阅（Pub/Sub）服务，旨在帮助用户实现分布式系统、微服务和服务器无关架构中的异步通信**。通过 SNS，用户可以将消息从一个发布者发送到多个订阅者（如应用程序、终端用户或其他服务），实现高效的消息传递和通知功能。

## Amazon Simple Queue Service
Amazon Simple Queue Service (Amazon SQS) 是 Amazon Web Services (AWS) 提供的一种完全托管的消息队列服务，旨在帮助用户在分布式系统、微服务和无服务器架构中实现异步通信。通过 SQS，用户可以解耦应用程序的组件，确保消息的可靠传递，并提高系统的弹性和可扩展性。

### 对比总结
简单来说：
* 如果需要点对点通信（生产者与消费者一对一），选择 Amazon SQS。
* 如果需要一对多的广播消息（发布者与多个订阅者），选择 Amazon SNS。

## AWS Step Functions
AWS Step Functions 是 AWS 提供的一项 **可视化工作流编排服务，用于构建和运行分布式应用程序、自动化任务和微服务架构**。它通过定义状态机（State Machine），将多个 AWS 服务或自定义任务组织成一个有序的工作流，并支持复杂的逻辑控制（如条件分支、并行执行、错误处理和重试机制）。

# 业务应用程序
## Amazon Connect
Amazon Connect 是 AWS 提供的一项 **云端联络中心服务，旨在帮助企业轻松建立和管理客户服务中心**。它是一种高度可扩展、经济高效且易于使用的解决方案，允许企业通过语音、聊天和其他渠道与客户进行互动。

Amazon Connect 的核心理念是简化联络中心的部署和运营，同时通过 AWS 的云服务提供高可用性、灵活性和智能化功能（如 AI 驱动的客户交互和分析）。它无需复杂的硬件或软件安装，用户可以快速启动并根据需求扩展。

## Amazon Simple Email Service
Amazon Simple Email Service (Amazon SES) 是 Amazon Web Services (AWS) 提供的 **一种灵活、可扩展且经济高效的云电子邮件服务**，专为开发人员和企业设计。它支持发送事务性邮件、营销邮件和批量邮件，同时也能接收和监控电子邮件。

# 客户参与
## AWS Activate(激活)
AWS Activate 是 Amazon Web Services (AWS) **专为初创公司设计的一项支持计划，旨在帮助初创公司快速启动和扩展其业务**。通过 AWS Activate，初创公司可以获得免费的 AWS 资源、技术支持、培训以及其他工具，以降低初期成本，加速产品开发，并实现快速增长。

## AWS IQ
AWS IQ 是 Amazon Web Services (AWS) 提供的一个平台，旨在 **帮助客户快速找到经过认证的 AWS 专家（包括个人和咨询公司），以获得技术支持、项目实施和解决方案开发服务**。通过 AWS IQ，客户可以直接与 AWS 认证专家进行协作，满足其在云计算上的各种需求。

## AWS Managed Services
AWS Managed Services (AMS) 是 Amazon Web Services 提供的一项托管服务，旨在 **帮助企业简化云环境的运营和管理**。AMS 通过自动化流程和专业支持，为客户提供安全、合规、高效的 AWS 环境管理服务，使企业能够专注于核心业务，而无需投入大量资源管理云基础设施。

# 开发工具
## AWS AppConfig
AWS AppConfig 是 Amazon Web Services (AWS) 提供的一项服务，隶属于 AWS Systems Manager，用于 **帮助开发者和运维团队快速、安全地管理和部署应用程序的配置数据**。它特别适用于需要频繁更新配置的应用程序，例如动态调整功能开关、修改应用程序行为或更新运行时参数，而无需重新部署代码。

## AWS Cloud9
AWS Cloud9 是 Amazon Web Services 提供的 **一款基于云的集成开发环境（IDE）**，允许开发者直接在浏览器中编写、运行和调试代码。它支持多种编程语言（如 JavaScript、Python、PHP 等），并且与 AWS 服务深度集成，使开发者可以快速构建、测试和部署应用程序。

## AWS CloudShell
AWS CloudShell 是 Amazon Web Services (AWS) 提供的 **一项基于浏览器的命令行界面 (CLI) 服务，允许用户在 AWS 管理控制台中直接运行命令来管理 AWS 资源**。它为用户提供了一个预配置的、基于云的 Shell 环境，无需额外安装或配置工具，即可快速开始使用 AWS CLI 和其他常用开发工具。

## AWS CodeCommit
AWS CodeCommit 是 AWS 提供的一项 **完全托管的源代码控制服务** ，支持团队安全地存储和管理代码、二进制文件或其他资产。它是基于 Git 的源代码管理工具，开发者可以像使用其他 Git 仓库（如 GitHub、GitLab、Bitbucket 等）一样使用 CodeCommit，但 CodeCommit 提供了更高的安全性、可扩展性和与 AWS 服务的深度集成。

## AWS CodeBuild
AWS CodeBuild 是 AWS 提供的一项 **完全托管的持续集成（CI）服务，用于自动化代码的构建、测试和打包** 。它能够从代码存储库中获取源代码，执行编译、运行单元测试，并生成可部署的构建工件（如二进制文件或容器镜像）。CodeBuild 是无服务器的，用户无需管理构建服务器，AWS 会根据需要自动分配和扩展资源。

## AWS CodePipeline
AWS CodePipeline 是 AWS 提供的一项 **完全托管的持续集成与持续交付（CI/CD）服务** ，用于自动化代码的构建、测试和部署流程。通过 CodePipeline，开发团队可以快速实现从代码提交到生产环境的自动化发布，确保应用程序的高质量和快速交付。

## AWS CodeDeploy
AWS CodeDeploy 是一项由 AWS 提供的 **全托管部署服务**，用于自动化代码部署到各种计算服务上，如 Amazon EC2 实例、本地服务器、AWS Lambda 函数 或 Amazon ECS 服务。它帮助开发者快速、安全地将应用程序的新版本部署到目标环境中，同时最大限度地减少停机时间和部署失败的风险。

## AWS CodeStar
AWS CodeStar 是 Amazon Web Services 提供的一项 **集成开发服务，旨在帮助用户快速设置、管理和部署应用程序的开发项目**。它提供了一个统一的界面，整合了多种 AWS 开发工具（如 CodeCommit、CodeBuild、CodePipeline 和 CodeDeploy），使开发团队能够快速启动项目并实现持续集成与持续交付（CI/CD）。

# 管理和监管
## AWS CloudFormation
AWS CloudFormation 是 AWS 提供的 **一项基础设施即代码（Infrastructure as Code, IaC）服务**，允许用户通过编写模板文件来定义和管理 AWS 资源。

## AWS X-Ray
AWS X-Ray 是一项分布式跟踪服务， **主要用于分析和调试分布式应用程序（如微服务架构）的性能问题** 。它帮助开发者和运维团队可视化应用程序的运行状况，识别性能瓶颈，并快速诊断故障。

通过 AWS X-Ray，您可以查看请求在应用程序中的完整路径，跟踪每个服务、组件、数据库查询、外部 API 调用等的性能表现，从而深入了解系统的行为和性能。

# 云财务管理
## AWS Budgets(预算)
AWS Budgets 是 Amazon Web Services (AWS) 提供的一项 **成本管理工具，旨在帮助用户设置、监控和控制其云服务的成本和使用情况**。通过 AWS Budgets，用户可以创建预算目标，与实际的成本或使用量进行对比，并在超出预算阈值或接近预算时收到通知。

## AWS Cost Explorer
AWS Cost Explorer 是 Amazon Web Services (AWS) 提供的一款 **成本分析和可视化工具，帮助用户深入了解其 AWS 服务的成本和使用情况**。通过 Cost Explorer，用户可以轻松生成定制化的报告，分析历史支出、预测未来成本，并识别潜在的节省机会。

## AWS Billing Conductor(指挥)
AWS Billing Conductor（AWS 账单指挥官） 是 AWS 提供的一项 **账单管理服务，专为需要为多个账户（如组织中的部门、团队或客户）定制账单的用户设计**。它允许用户创建自定义的账单模型，重新分摊和分配成本，以满足内部成本分配或外部客户计费的需求。

## AWS Cost and Usage Report
AWS 成本和使用情况报告（AWS Cost and Usage Report, CUR） 是 AWS 提供的一种 **全面的成本和使用情况分析工具。它可以帮助用户详细了解其 AWS 服务的使用情况和相关成本，支持从高层概览到细粒度的分析**。CUR 是 AWS 成本管理套件中的核心工具之一，通常用于优化成本、预算管理和财务分析。

## AWS Knowledge Center
AWS Knowledge Center 是 Amazon Web Services (AWS) 提供的 **一个在线知识库，旨在帮助用户快速解决常见问题、了解 AWS 服务的最佳实践，并获取技术支持的相关信息**。它是一个自助式资源中心，汇集了 AWS 客户支持团队整理的常见问题解答（FAQs）和解决方案。

## AWS re:Post
AWS re:Post 是 AWS 提供的一个 **基于社区的问答平台，旨在帮助用户分享知识、解决问题并学习 AWS 服务和解决方案**。AWS re:Post 是 AWS Support 的一部分，作为 AWS 论坛的升级版，提供了更现代化的用户体验和功能，支持用户之间的互动与协作。