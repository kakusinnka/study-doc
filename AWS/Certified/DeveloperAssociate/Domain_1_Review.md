# Domain 1 Review: AWS Certified Developer - Associate (DVA-C02 - English)
* 为 AWS 上托管的应用程序开发代码
* 为 AWS Lambda 开发代码
* 在应用程序开发中使用数据存储
* 专注于构建、维护和创新高可用性应用程序的核心功能

# 第一课：领域 1 导论
## 任务声明 1.1：为 AWS 上托管的应用程序开发代码
对于第一个任务陈述，开发包括配置和使用 SDK、API 凭证、密钥、身份在 Amazon EC2 实例上运行应用程序、定制网络、管理资源以及开发应用程序。  
确保您知道如何为具有不同架构模式的应用程序编写代码，例如事件驱动、微服务、编排、业务流程和扇出。  
还有，如何为容错设计模式编写代码，例如具有指数退避和抖动的重试以及死信队列。  
您需要了解如何创建、扩展和维护 API，并了解使用不同 AWS 服务（例如 Amazon API Gateway、AWS Lambda、Amazon DynamoDB、Amazon S3 和 Amazon SQS）的 API 操作。  
确保您了解方法请求、方法响应、集成请求、集成响应、强制验证规则、覆盖状态代码、映射模板、阶段、变量、缓存、限制等。  
这应该包括 AWS 无服务器服务的设计、开发和用例，包括设计模式和微服务设计模式。  
该考试不针对特定语言进行测试，因为 AWS 支持所有考生对不同语言的深度理解，但您也应该了解编码最佳实践和错误处理。  

## 任务声明 1.2：为 AWS Lambda 开发代码
此新版本将要求您更深入地开发 AWS Lambda 代码。对于第二个任务说明，请确保您可以通过定义环境变量和配置参数（例如内存、并发性、超时、运行时、处理程序、层、扩展、触发器和目标）来配置 Lambda 函数。  

## 任务声明 1.3：在应用程序开发中使用数据存储
对于第三个任务说明，深入了解 AWS 存储选项，特别关注应用程序开发中数据存储的要求和用例。  
确保您了解如何使用、管理和维护数据存储以及管理数据生命周期。  
了解不同的数据缓存服务、缓存策略、临时和持久数据存储模式以及数据库一致性模型以及何时使用它们。  
确保您知道如何根据您的需求或迁移选择正确的数据库服务，以及如何配置加密以确保您的数据安全，这将在领域 2：安全性中详细介绍。  

# 第二课：为托管在 AWS 上的应用程序开发代码
在 AWS 环境中开发应用程序代码的核心支柱是 **卓越运营支柱**，其目标是通过高效支持工作负载的开发与运行，洞察运行状况，并持续优化流程与规范以创造业务价值。以下是关键要点：

## 核心理念：
1. **开发规范的延伸**：将应用程序代码的开发规范扩展至整个 AWS 环境，例如通过事件触发部署实现自动化，并跨团队/组织共享成果以提升开发效益。
2. **安全实验与优化**：在 AWS 上通过实验完善工作负载，优化运维流程，并实践故障处理。

## 推荐工具：
- **AWS CloudFormation**：用于基础设施即代码管理。
- **AWS 无服务器应用程序模型（SAM）**：用于构建和部署无服务器应用程序。

## 架构设计模式：
1. **理解工作负载及行为**：设计应用程序时需充分了解工作负载的预期行为，并增强状态可见性以优化运维流程。
2. **关键问题**：
   - 应用程序的访问方式及使用模式。
   - 硬件管理需求。
   - 开发与部署模式。
   - 应用程序的运作方式。

## 事件驱动架构：
- **事件驱动设计**：促进服务解耦，支持微服务架构。
- **紧密耦合与松散耦合**：需掌握两者的区别。
- **事件源与事件处理**：多数 AWS 服务可生成事件，且许多服务可充当事件源（如 AWS Lambda）。

## 
* AWS 架构设计框架及其六大支柱
* 开发应用程序代码的核心支柱是卓越运营支柱
* AWS CloudFormation
* AWS 无服务器应用程序模型（AWS Serverless Application Model）
* 采用事件驱动架构
* 紧密耦合与松散耦合组件的区别
* AWS 无服务器服务（如 Amazon SQS、SNS、EventBridge）编写并构建事件驱动型应用
* 带抖动的指数退避策略
* 使用 Lambda 将调用发送至其他服务，如 SQS、EventBridge 或 SNS
* 借助 AWS Step Functions 实现重试机制，包括设置重试间隔、后退速率、最大尝试次数、时间间隔和超时值
* 使用 Step Functions 替代直接调用系统来执行任务
* 若需协调多服务间的状态变更，Amazon EventBridge 可能是更优选择
* 扇出模式
* 幂等函数
* 理解同步与异步模式
* 无状态与有状态设计
* AWS SDKs
* 使用 Amazon ECS、Lambda、Cognito、API 网关、CloudFront、Amazon DynamoDB 和 S3 实现的微服务设计模式
* API 网关知识：方法请求与响应、集成请求与响应、映射模板、阶段与阶段变量、缓存及速率限制机制，同时理解使用计划与 API 密钥管理
* 托管流式数据服务：Amazon Kinesis Data Streams、Amazon Data Firehose、Amazon Managed Streaming for Apache Kafka、Apache Flume、Apache Spark Streaming 及 Apache Storm
* CodeBuild
* 编写和运行单元测试的能力：AWS SAM、CodePipeline 和 CloudFormation
* 确保用户资料数据在设备间同步以提升用户体验：集成 AWS Amplify、Cognito 身份池、Cognito 用户池还是 **Cognito Sync**？
* DynamoDB 表中的热点分区
* CloudWatch 日志
* 深入理解如何在 AWS 微服务架构中运用各项服务，包括 Amazon SQS、Amazon SNS、Amazon Kinesis 数据流、Amazon Kinesis 服务、Amazon DynamoDB 流、AWS 物联网、Amazon MQ 及 AWS Step Functions。

## 第三课：为 AWS Lambda 开发代码
* 