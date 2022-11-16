# Cloud Logging
全代管式实时日志管理功能，提供 EB 级的存储、搜索、分析和提醒服务。

## 产品概述
https://cloud.google.com/logging

## 快速入门
### 快速入门：使用 Logging 工具
* 使用 gcloud CLI 写入日志条目
Logging 支持包含结构化（Json）和非结构化数据（字符串）的日志条目。
```
gcloud logging write my-test-log "A simple entry."

gcloud logging write --payload-type=json my-test-log '{ "message": "My second entry", "weather": "partly cloudy"}'
```

* 使用 gcloud CLI 列出日志条目
```
gcloud logging read "resource.type=global"
```

* 使用 API Explorer 列出日志条目
```
https://cloud.google.com/logging/docs/reference/v2/rest/v2/entries/list

https://cloud.google.com/logging/docs/api
```

* 在日志浏览器中查看日志条目  
如需在 Google Cloud Console 中查看日志条目，您可以使用日志浏览器。大多数 Cloud 项目会存储大量日志；您可以通过编写查询来选择某些日志条目。

* 在日志浏览器中查询日志条目  
您可以使用查询编辑器查询日志条目；对于结构化日志，也可以使用键和值查询日志条目。

* 问题排查

### 快速入门：使用 Python
暂时跳过

### 快速入门：针对 Compute Engine 虚拟机的日志记录
暂时跳过

## 示例
暂时跳过

## 方法指南
### 使用 Logging 库
* Logging 库概览：许多编程语言都有标准的日志编写接口，您可以重新配置这些接口以使用 Logging。
* 要将日志写入 Logging，您可以执行以下任何操作：
  - 将日志写入现有日志文件，例如 VM 实例上的 syslog。 Logging 代理将日志发送到 Google Cloud 的操作套件。
  - 配置标准日志记录包以将您写入的日志发送到 Logging。
  - 使用 Logging 的客户端库为您的编程语言调用 Logging API。
  - 直接调用 Logging API REST 端点。
  - 使用 gcloud CLI。 有关更多信息，请参阅 [gcloud logging](https://cloud.google.com/logging/docs/reference/tools/gcloud-logging) 命令行界面。

* Reading logs:
  - Use the Logs Explorer in the Google Cloud console.
  - Call the Logging API through the [Client Libraries](https://cloud.google.com/logging/docs/reference/libraries) for your programming language.
  - Call the Logging API REST endpoints directly. See the [Logging API reference documentation](https://cloud.google.com/logging/docs/reference/v2/rest).
  - 使用 gcloud CLI。 有关更多信息，请参阅 [gcloud logging](https://cloud.google.com/logging/docs/reference/tools/gcloud-logging) 命令行界面。

* Setting Up Cloud Logging for Java
  - 您可以使用 Logback appender 或 java.util.logging 处理程序将日志从Java应用程序写入 Cloud Logging，也可以直接使用 Java 版 Cloud Logging 库。

* 设置 Python 版 Cloud Logging
使用 Logging 客户端库随附的 Python 日志记录处理程序，或者直接使用 Python 版 Cloud Logging API Cloud 客户端库，可以从 Python 应用向 Logging 写入日志。
  - 配置日志记录处理程序(Configuring the logging handler): 整合 Google Cloud Logging client 和 Python logging
  - [Python Client for Cloud Logging](https://googleapis.dev/python/logging/latest/index.html)