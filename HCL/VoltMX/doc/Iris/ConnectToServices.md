# 连接到服务
Service 是一个应用程序组件，它表示应用程序与外部服务数据源的交互。服务定义包括与外部数据源交换数据所需的元数据或配置。例如，配置可以是：服务类型、服务 ID、输入参数、输出参数、前处理器和后处理器、目标 URL、身份验证凭据（如果需要）和类型 （HTTP/HTTPS）。

您可以为以下连接器定义服务：
* XML over HTTP
* Simple Object Access Protocol (SOAP)
* Java - 任何其他数据源的自定义连接器
* 复合 - 以上所有的组合

Volt MX Foundry 支持以下服务：
* XML
* SOAP
* [JSON](./ServiceJSON.md)
* [Java](./ServiceJava.md)
* JavaScript
* API Proxy
* Mock Data
* VoltMX SAP Gateway
* MuleSoft
* AWS API Gateway
* Database
* MongoDB
* RAML
* SAP JCo
* IBM MQ
* Salesforce
* Open API (Swagger)