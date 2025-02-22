# 考试范围内的 AWS 服务和功能

## 1. 分析服务
### 1.1 Amazon Athena
Amazon Athena 是一种交互式查询服务，允许用户使用标准 SQL 查询存储在 Amazon S3 中的数据。它无需设置基础设施，用户只需为查询的数据付费。Athena 支持多种数据格式（如 CSV、JSON 和 Parquet），适合快速分析大规模数据集。

### 1.2 AWS Data Exchange
AWS Data Exchange 使客户能够轻松访问和使用第三方数据集。用户可以从多个供应商获取数据，并将其集成到自己的应用程序中，支持数据驱动的决策和分析。

### 1.3 Amazon EMR
Amazon EMR（Elastic MapReduce）是一项托管的大数据处理服务，支持 Hadoop、Spark 和其他大数据框架。用户可以快速处理和分析大规模数据集，自动化集群的配置和管理，适合大数据分析和机器学习工作负载。

### 1.4 AWS Glue
AWS Glue 是一项全面的 ETL（提取、转换、加载）服务，帮助用户准备和加载数据以进行分析。它自动发现数据并生成 ETL 代码，简化数据集成流程，适合数据仓库和数据湖的构建。

### 1.5 Amazon Kinesis
Amazon Kinesis 是用于实时数据流处理的服务，支持数据采集、处理和分析。用户可以构建实时应用程序，处理来自多个数据源的数据流，如网站点击流、社交媒体数据和传感器数据。

### 1.6 Amazon Managed Streaming for Apache Kafka (Amazon MSK)
Amazon MSK 是一种托管的 Apache Kafka 服务，简化了流数据应用的构建和管理。用户可以轻松设置和运行 Kafka 集群，处理实时数据流，适合大规模数据处理和事件驱动架构。

### 1.7 Amazon OpenSearch Service
Amazon OpenSearch Service 是基于 Elasticsearch 的托管搜索和分析服务，支持实时数据搜索和分析。用户可以构建和管理搜索应用程序，分析日志和指标数据，适合监控和日志分析。

### 1.8 Amazon QuickSight
Amazon QuickSight 是一项商业智能服务，提供数据可视化和仪表盘功能。用户可以快速创建交互式报告，支持多种数据源的连接和分析，适合业务智能和数据分析。

### 1.9 Amazon Redshift
Amazon Redshift 是高速、可扩展的数据仓库服务，支持复杂查询和分析大规模数据集。用户可以轻松地从多种数据源加载数据，并执行快速分析，适合数据驱动的决策。

## 2. 应用程序集成服务
### 2.1 Amazon EventBridge
Amazon EventBridge 是一种事件总线服务，允许不同应用程序和服务之间的事件驱动通信。用户可以创建事件规则，自动触发目标服务以响应事件，适合微服务架构。

### 2.2 Amazon Simple Notification Service (Amazon SNS)
Amazon SNS 是用于发送通知和消息到多个订阅者的消息传递服务。用户可以通过电子邮件、短信或移动推送通知等多种方式发送消息，适合实时通知和警报。

### 2.3 Amazon Simple Queue Service (Amazon SQS)
Amazon SQS 是一种托管的消息队列服务，支持解耦和扩展微服务架构。用户可以在不同组件之间安全地传递消息，确保消息的可靠性和顺序，适合异步处理。

### 2.4 AWS Step Functions
AWS Step Functions 是用于构建和协调微服务工作流的服务。用户可以定义复杂的工作流，自动化应用程序的各个步骤，支持状态管理和错误处理。

## 3. 业务应用程序
### 3.1 Amazon Connect
Amazon Connect 是基于云的联络中心服务，提供客户服务解决方案。用户可以轻松设置和管理呼叫中心，支持语音、聊天等多种沟通方式，适合客户支持和服务。

### 3.2 Amazon Simple Email Service (Amazon SES)
Amazon SES 是用于发送和接收电子邮件的托管服务，适合营销和通知。用户可以轻松发送大批量电子邮件，支持高送达率和可扩展性，适合电子邮件营销。

## 4. 云财务管理
### 4.1 AWS Billing Conductor
AWS Billing Conductor 是用于自定义账单和费用管理的工具，允许用户根据需求生成和管理账单，支持多种计费模式。

### 4.2 AWS Budgets
AWS Budgets 允许用户设置预算并监控费用，确保支出控制在预期范围内。用户可以设置警报，及时获得预算超支的通知。

### 4.3 AWS 成本和使用情况报告
AWS 成本和使用情况报告提供详细的费用和使用情况分析，帮助用户了解资源使用情况和成本分布，支持财务管理。

### 4.4 AWS Cost Explorer
AWS Cost Explorer 是用于可视化和分析 AWS 成本和使用情况的工具，支持历史数据查看和趋势分析，帮助用户优化支出。

### 4.5 AWS Marketplace
AWS Marketplace 是提供各种软件和服务的在线市场，用户可以方便地购买和部署所需的应用程序和服务，支持快速集成。

## 5. 计算服务
### 5.1 AWS Batch
AWS Batch 是一种用于批量计算的服务，自动管理计算资源，优化任务处理。用户可以运行数千个批处理作业，按需分配资源，适合大规模数据处理。

### 5.2 Amazon EC2
Amazon EC2（Elastic Compute Cloud）是一项提供可扩展虚拟服务器的服务，支持多种操作系统和应用程序。用户可以根据需求快速启动和管理实例，适合各种计算工作负载。

### 5.3 AWS Elastic Beanstalk
AWS Elastic Beanstalk 是用于快速部署和管理应用程序的服务，支持多种开发语言和平台。用户可以专注于代码，而无需管理基础设施，适合开发和测试环境。

### 5.4 Amazon Lightsail
Amazon Lightsail 是一种简化的云计算服务，适合小型项目和应用，提供简单的定价模型和易于使用的界面，支持快速启动和管理。

### 5.5 AWS Local Zones
AWS Local Zones 在离用户更近的地方提供低延迟的计算资源，支持边缘计算和延迟敏感的应用，适合游戏和媒体处理。

### 5.6 AWS Outposts
AWS Outposts 是将 AWS 基础设施扩展到本地数据中心的服务，支持混合云架构，允许用户在本地运行 AWS 服务，适合合规性和延迟要求高的应用。

### 5.7 AWS Wavelength
AWS Wavelength 在 5G 网络边缘提供低延迟应用的服务，适合实时应用场景，如自动驾驶和增强现实，支持边缘计算。

## 6. 容器服务
### 6.1 Amazon Elastic Container Registry (Amazon ECR)
Amazon ECR 是一种托管 Docker 容器镜像的服务，支持容器化应用的管理和部署，适合微服务架构。

### 6.2 Amazon Elastic Container Service (Amazon ECS)
Amazon ECS 是用于容器编排和管理的服务，支持 Docker 容器的运行和管理，适合大规模容器化应用。

### 6.3 Amazon Elastic Kubernetes Service (Amazon EKS)
Amazon EKS 是一种托管的 Kubernetes 服务，简化容器化应用的管理和扩展，支持自动化集群管理，适合云原生应用。

## 7. 数据库服务
### 7.1 Amazon Aurora
Amazon Aurora 是兼容 MySQL 和 PostgreSQL 的高性能关系数据库，提供自动扩展和高可用性，支持大规模应用和事务处理。

### 7.2 Amazon DynamoDB
Amazon DynamoDB 是完全托管的 NoSQL 数据库，支持高性能和可扩展性，适合大规模应用和实时数据处理，提供低延迟访问。

### 7.3 Amazon MemoryDB for Redis
Amazon MemoryDB 是一种托管的 Redis 兼容内存数据库服务，支持高速数据访问和持久化，适合缓存和实时分析。

### 7.4 Amazon Neptune
Amazon Neptune 是图数据库服务，支持图形查询，适合社交网络、推荐系统等应用，支持复杂关系数据的存储和查询。

### 7.5 Amazon RDS
Amazon RDS（Relational Database Service）是托管的关系数据库服务，支持多种数据库引擎，简化数据库管理和维护，适合企业级应用。

## 8. 开发工具
### 8.1 AWS AppConfig
AWS AppConfig 是用于管理应用程序配置的服务，支持动态配置更新，确保应用程序的灵活性和可用性。

### 8.2 AWS CLI
AWS CLI（Command Line Interface）是命令行工具，允许用户与 AWS 服务进行交互和管理，适合自动化操作和脚本编写。

### 8.3 AWS Cloud9
AWS Cloud9 是基于云的集成开发环境 (IDE)，支持实时协作和代码编辑，适合团队开发和快速原型设计。

### 8.4 AWS CloudShell
AWS CloudShell 是浏览器中运行的命令行界面，提供直接访问 AWS 资源的能力，支持快速操作和管理。

### 8.5 AWS CodeArtifact
AWS CodeArtifact 是用于存储和共享软件包的服务，支持多种包格式，简化软件开发过程和版本管理。

### 8.6 AWS CodeBuild
AWS CodeBuild 是完全托管的构建服务，自动化构建过程，支持持续集成和快速发布，适合 DevOps 流程。

### 8.7 AWS CodeCommit
AWS CodeCommit 是托管的 Git 版本控制服务，支持代码管理和协作开发，适合团队协作和代码审查。

### 8.8 AWS CodeDeploy
AWS CodeDeploy 是自动化应用程序部署的服务，支持多种部署策略，确保应用的高可用性和快速发布。

### 8.9 AWS CodePipeline
AWS CodePipeline 是持续集成和持续交付的服务，自动化软件发布流程，支持快速迭代和发布，适合 DevOps 实践。

### 8.10 AWS CodeStar
AWS CodeStar 是用于快速开发和管理应用程序的服务，提供集成开发环境和项目管理工具，适合团队协作。

### 8.11 AWS X-Ray
AWS X-Ray 是用于分析和调试应用程序的服务，帮助识别性能瓶颈和错误，支持可视化分析和故障排除。

## 9. 终端用户计算
### 9.1 Amazon AppStream 2.0
Amazon AppStream 2.0 是托管的应用程序流服务，允许用户在浏览器中访问桌面应用，支持远程工作和安全访问。

### 9.2 Amazon WorkSpaces
Amazon WorkSpaces 是托管的虚拟桌面服务，支持远程工作和安全访问，提供灵活的桌面解决方案，适合企业和教育机构。

### 9.3 Amazon WorkSpaces Web
Amazon WorkSpaces Web 是用于访问 WorkSpaces 的 Web 界面，提供灵活的访问方式，支持多种设备和平台。

## 10. 前端 Web 和移动服务
### 10.1 AWS Amplify
AWS Amplify 是用于构建和部署全栈应用程序的服务，支持快速开发和集成，简化前端和后端的连接，适合快速交付应用。

### 10.2 AWS AppSync
AWS AppSync 是用于构建 GraphQL API 的服务，支持实时数据更新和离线访问，适合现代应用程序的开发。

### 10.3 AWS Device Farm
AWS Device Farm 是用于测试移动和 Web 应用的服务，支持多种设备和操作系统，确保应用的兼容性和性能。

## 11. 物联网 (IoT) 服务
### 11.1 AWS IoT Core
AWS IoT Core 是用于连接和管理 IoT 设备的服务，支持安全通信和数据处理，适合智能家居和工业 IoT 应用。

### 11.2 AWS IoT Greengrass
AWS IoT Greengrass 是用于在边缘设备上运行 AWS Lambda 函数的服务，支持本地计算和智能设备的管理，适合延迟敏感的应用。

## 12. 机器学习服务
### 12.1 Amazon Comprehend
Amazon Comprehend 是自然语言处理服务，分析文本并提取信息，如情感分析和主题建模，适合文本数据处理。

### 12.2 Amazon Kendra
Amazon Kendra 是智能搜索服务，提供企业级搜索功能，支持自然语言查询，帮助用户快速找到所需信息。

### 12.3 Amazon Lex
Amazon Lex 是用于构建对话式接口的服务，支持语音和文本输入，适合聊天机器人和语音助手的开发。

### 12.4 Amazon Polly
Amazon Polly 是文本转语音服务，支持多种语言和声音选项，适合创建语音应用和音频内容。

### 12.5 Amazon Rekognition
Amazon Rekognition 是图像和视频分析服务，支持面部识别、对象检测和内容审核，适合安全和媒体应用。

### 12.6 Amazon SageMaker
Amazon SageMaker 是用于构建、训练和部署机器学习模型的服务，支持全生命周期管理，简化机器学习流程。

### 12.7 Amazon Textract
Amazon Textract 是用于自动提取文档中的文本和数据的服务，支持多种文档格式，适合文档处理和数据录入。

### 12.8 Amazon Transcribe
Amazon Transcribe 是语音转文本服务，支持实时和批量处理，适合会议记录和字幕生成。

### 12.9 Amazon Translate
Amazon Translate 是翻译服务，支持多种语言的文本翻译，适合跨语言内容的创建和管理。

## 13. 管理和监管服务
### 13.1 AWS Auto Scaling
AWS Auto Scaling 是自动调整计算资源的服务，支持按需扩展和缩减，确保应用的高可用性和性能。

### 13.2 AWS CloudFormation
AWS CloudFormation 是基础设施即代码服务，允许用户以代码方式管理 AWS 资源，支持资源的自动化部署。

### 13.3 AWS CloudTrail
AWS CloudTrail 是用于记录和监控 AWS 账户活动的服务，支持安全审计和合规性检查，帮助用户跟踪资源变更。

### 13.4 Amazon CloudWatch
Amazon CloudWatch 是监控与管理 AWS 资源和应用程序的服务，支持日志和指标分析，帮助用户优化性能和故障排除。

### 13.5 AWS Compute Optimizer
AWS Compute Optimizer 是用于优化计算资源使用的服务，提供性能建议，帮助用户降低成本并提高效率。

### 13.6 AWS Config
AWS Config 是用于管理和审计 AWS 资源配置的服务，支持合规性检查和资源变更跟踪，帮助用户确保资源符合最佳实践。

### 13.7 AWS Control Tower
AWS Control Tower 是用于设置和管理多账户 AWS 环境的服务，支持最佳实践和合规性管理，帮助用户快速启动和管理 AWS 账户。

### 13.8 AWS Health Dashboard
AWS Health Dashboard 提供 AWS 服务健康状态的服务，支持事件通知和故障排除，帮助用户及时了解服务中断和维护情况。

### 13.9 AWS Launch Wizard
AWS Launch Wizard 是用于简化 AWS 资源部署的服务，支持向导式配置，帮助用户快速启动应用程序和资源。

### 13.10 AWS License Manager
AWS License Manager 是用于管理软件许可证的服务，支持合规性管理和许可证跟踪，帮助用户优化许可证使用。

### 13.11 AWS 管理控制台
AWS 管理控制台是 Web 界面，用于管理 AWS 服务和资源，提供可视化操作和管理工具，适合用户进行实时监控和管理。

### 13.12 AWS Organizations
AWS Organizations 是用于集中管理多个 AWS 账户的服务，支持策略管理和账单整合，帮助用户降低成本并提高安全性。

### 13.13 AWS Resource Groups and Tag Editor
AWS Resource Groups 和 Tag Editor 是用于组织和管理 AWS 资源的服务，支持标签管理和资源分组，帮助用户优化资源管理。

### 13.14 AWS Service Catalog
AWS Service Catalog 是用于创建和管理 AWS 资源目录的服务，支持自助服务和资源管理，帮助用户快速访问和部署所需资源。

### 13.15 AWS Systems Manager
AWS Systems Manager 是用于管理和自动化 AWS 资源的服务，支持操作管理和资源监控，帮助用户提高运维效率。

### 13.16 AWS Trusted Advisor
AWS Trusted Advisor 是提供最佳实践建议的服务，帮助用户优化 AWS 使用和成本管理，确保资源的高效利用。

### 13.17 AWS Well-Architected Tool
AWS Well-Architected Tool 是用于评估和优化 AWS 架构的工具，支持最佳实践审核和改进建议，帮助用户构建可靠、安全和高效的应用。

## 14. 迁移和传输服务
### 14.1 AWS Application Discovery Service
AWS Application Discovery Service 是用于发现和评估本地应用程序的服务，支持迁移规划和资源评估，帮助用户制定有效的迁移策略。

### 14.2 AWS Application Migration Service
AWS Application Migration Service 是简化应用程序迁移到 AWS 的服务，支持自动化迁移过程，降低迁移成本，帮助用户快速迁移应用。

### 14.3 AWS Database Migration Service (AWS DMS)
AWS DMS 是用于将数据库迁移到 AWS 的服务，支持多种数据库引擎，确保数据的安全和完整性，帮助用户无缝迁移数据。

### 14.4 AWS Migration Hub
AWS Migration Hub 提供迁移进度跟踪的服务，支持多种迁移工具的集成，帮助用户管理迁移过程中的各个阶段，确保迁移的顺利进行。

### 14.5 AWS Schema Conversion Tool (AWS SCT)
AWS SCT 是用于数据库架构转换的工具，支持不同数据库之间的迁移，帮助用户自动化架构转换，简化迁移流程。

### 14.6 AWS Snow Family
AWS Snow Family 是用于大规模数据迁移的硬件设备，支持离线数据传输，适合带宽受限的环境，帮助用户安全高效地移动大量数据。

### 14.7 AWS Transfer Family
AWS Transfer Family 是用于安全传输文件到和从 AWS 的服务，支持多种协议（如 SFTP、FTP），确保数据传输的安全性和可靠性。

## 15. 联网和内容分发
### 15.1 Amazon API Gateway
Amazon API Gateway 是用于创建和发布 API 的服务，支持 RESTful 和 WebSocket API，简化 API 管理和监控，适合构建现代应用程序。

### 15.2 Amazon CloudFront
Amazon CloudFront 是全球内容分发网络 (CDN) 服务，支持加速静态和动态内容交付，提高用户访问速度，适合网站和应用程序的内容分发。

### 15.3 AWS Direct Connect
AWS Direct Connect 是用于直接连接本地数据中心与 AWS 的服务，支持私有连接，降低网络延迟和成本，适合需要高带宽和低延迟的应用。

### 15.4 AWS Global Accelerator
AWS Global Accelerator 是用于优化应用程序性能的服务，提供全球流量管理，确保用户连接到最佳区域，提高应用的可用性和响应速度。

### 15.5 Amazon Route 53
Amazon Route 53 是可扩展的域名系统 (DNS) 服务，支持域名解析和流量路由，确保高可用性和低延迟，适合网站和应用的域名管理。

### 15.6 Amazon VPC
Amazon VPC（Virtual Private Cloud）是虚拟私有云服务，用于隔离和管理 AWS 资源，支持网络配置和安全管理，适合构建安全的网络架构。

### 15.7 AWS VPN
AWS VPN 是用于安全连接本地网络与 AWS 的服务，支持加密通信，确保数据传输的安全性，适合需要安全连接的企业应用。

## 16. 安全性、身份和合规性
### 16.1 AWS Artifact
AWS Artifact 是提供合规性报告和文档的服务，支持审计需求，帮助用户获取和管理合规性相关的文档。

### 16.2 AWS Audit Manager
AWS Audit Manager 是用于自动化审计和合规检查的服务，支持报告生成，帮助用户简化合规性管理。

### 16.3 AWS Certificate Manager (ACM)
AWS Certificate Manager 是用于管理 SSL/TLS 证书的服务，支持证书的申请、管理和部署，确保网站和应用的安全性。

### 16.4 AWS CloudHSM
AWS CloudHSM 是提供硬件安全模块的服务，支持密钥管理和加密，确保数据安全，适合需要高安全性的应用。

### 16.5 Amazon Cognito
Amazon Cognito 是用于用户身份验证和管理的服务，支持社交登录和多因素认证，帮助用户管理应用的用户身份。

### 16.6 Amazon Detective
Amazon Detective 是用于安全事件调查和分析的服务，支持数据关联，帮助用户快速识别和响应安全事件。

### 16.7 AWS Directory Service
AWS Directory Service 是提供托管目录服务的解决方案，支持 Active Directory 集成，帮助用户管理用户和权限。

### 16.8 AWS Firewall Manager
AWS Firewall Manager 是用于集中管理 AWS WAF 规则的服务，支持安全策略管理，帮助用户保护应用免受常见攻击。

### 16.9 Amazon GuardDuty
Amazon GuardDuty 是威胁检测服务，提供恶意活动监控和警报，帮助用户识别和响应潜在的安全威胁。

### 16.10 AWS Identity and Access Management (IAM)
AWS IAM 是用于管理用户和权限的服务，支持细粒度访问控制，确保用户和资源的安全性。

### 16.11 AWS IAM Identity Center (AWS Single Sign-On)
AWS IAM Identity Center 是用于集中管理用户访问的服务，支持单点登录，简化用户身份管理。

### 16.12 Amazon Inspector
Amazon Inspector 是自动化安全评估服务，支持漏洞扫描和合规性检查，帮助用户识别和修复安全风险。

### 16.13 AWS Key Management Service (AWS KMS)
AWS KMS 是用于管理加密密钥的服务，支持数据加密和解密，确保数据的安全性和合规性。

### 16.14 Amazon Macie
Amazon Macie 是用于识别和保护敏感数据的服务，支持数据隐私管理，帮助用户遵循合规性要求。

### 16.15 AWS Network Firewall
AWS Network Firewall 是提供网络安全防护的服务，支持流量过滤和监控，帮助用户保护网络边界。

### 16.16 AWS Resource Access Manager (AWS RAM)
AWS RAM 是用于共享 AWS 资源的服务，支持跨账户访问，帮助用户优化资源使用。

### 16.17 AWS Secrets Manager
AWS Secrets Manager 是用于安全管理和访问密钥的服务，支持秘密存储和轮换，帮助用户保护敏感信息。

### 16.18 AWS Security Hub
AWS Security Hub 是集中安全管理和合规性检查的服务，支持多种安全工具集成，帮助用户获得全面的安全态势。

### 16.19 AWS Shield
AWS Shield 是 DDoS 防护服务，提供自动化的攻击防御，帮助用户保护应用免受流量攻击。

### 16.20 AWS WAF
AWS WAF 是 Web 应用防火墙，用于保护应用程序免受常见攻击，支持自定义规则和监控。

## 17. 无服务器服务
### 17.1 AWS Fargate
AWS Fargate 是无服务器计算引擎，用于容器化应用，支持自动扩展，简化容器管理，适合微服务架构。

### 17.2 AWS Lambda
AWS Lambda 是无服务器计算服务，允许用户运行代码而无需管理服务器，支持事件驱动架构，适合自动化和实时处理。

## 18. 存储服务
### 18.1 AWS Backup
AWS Backup 是集中管理和自动化备份的服务，支持多种 AWS 资源，确保数据的安全和可恢复性。

### 18.2 Amazon Elastic Block Store (Amazon EBS)
Amazon EBS 是提供持久性块存储的服务，支持高性能应用，适合与 Amazon EC2 实例配合使用。

### 18.3 Amazon Elastic File System (Amazon EFS)
Amazon EFS 是可扩展的文件存储服务，支持多种实例访问，适合共享文件存储和大数据分析。

### 18.4 AWS Elastic Disaster Recovery
AWS Elastic Disaster Recovery 是用于灾难恢复的服务，支持快速恢复应用程序，确保业务连续性。

### 18.5 Amazon FSx
Amazon FSx 为 Windows 和 Lustre 文件系统提供托管服务，支持高性能存储，适合企业级应用和高性能计算。

### 18.6 Amazon S3
Amazon S3 是对象存储服务，提供高可用性和耐久性，适合存储大规模数据，支持数据备份和恢复。

### 18.7 Amazon S3 Glacier
Amazon S3 Glacier 是低成本存储服务，用于长期归档数据，支持低频访问，适合数据存档和备份。

