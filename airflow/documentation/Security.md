# Security
## 访问控制 Access Control
Airflow Web 服务器 UI 的访问控制由 Flask AppBuilder (FAB) 处理。
* 默认角色: Airflow 默认附带一组角色：Admin、User、Op、Viewer 和 Public。只有 Admin 用户可以配置/更改其他角色的权限。但不建议对默认角色的权限进行更改。
  * Admin 用户拥有所有可能的权限，包括授予或撤销其他用户的权限。
  * Public 用户（匿名）没有任何权限。
  * Viewer 用户拥有有限的查看权限。
  * User 用户有 Viewer 权限，加上额外的用户权限。
  * Op 用户有 User 权限，加上额外的操作权限。
* 自定义角色
  * DAG 级别角色：Admin可以创建一组角色，这些角色只允许查看一组特定的 dags。这称为 DAG 级别访问。
* 权限
  * 基于资源的权限: 从 2.0 版开始，权限基于单个资源和对这些资源执行的一小部分操作。资源匹配标准的 Airflow 概念，例如 Dag、DagRun、Task 和 Connection。
操作包括 can_create、can_read、can_edit 和 can_delete。然后将权限（资源 + 操作）添加到角色。
  * DAG 级权限: 专门针对 DAG 级的权限，可以在所有DAG 或 单个DAG 对象的级别上控制访问。这包括 DAGs.can_create、DAGs.can_read、DAGs.can_edit 和 DAGs.can_delete。

## API
### API认证
* 禁用身份验证
* Kerberos 认证
* 基本认证
* 滚动您自己的 API 身份验证
### 启用 CORS
### 页面大小限制

## Flower
Flower 是一个基于 Web 的工具，用于监视和管理 Celery 集群。

## Kerberos
Airflow 初步支持 Kerberos。这意味着 Airflow 可以为自己更新 kerberos 票证并将其存储在票证缓存中。hooks 和 dags 可以使用 ticket 来验证基于 kerberos 的服务。
### 限制
* 启用kerberos
* 空气流动
### Hadoop
### 使用 kerberos 身份验证

## Webserver
本主题介绍如何配置 Airflow 以保护您的网络服务器。
### 在来自另一个站点的 Web 框架中呈现 Airflow UI
默认情况下启用在 Web 框架中使用 Airflow。要禁用此功能（并防止点击劫持攻击），请设置以下内容：
```
[webserver]
x_frame_enabled = False
```

### 敏感变量字段
根据变量名称被视为“敏感”的变量值将在 UI 中自动屏蔽。

### 网络认证
默认情况下，Airflow 要求用户在登录前指定密码。
* 密码: 最简单的身份验证机制之一是要求用户在登录前指定密码。
* 其他方法
* 将基于团队的授权与 Github OAuth 结合使用的示例
### SSL
可以通过提供证书和密钥来启用 SSL。

## Workload
本主题介绍如何配置 Airflow 以保护您的工作负载。
### 冒充
* 默认模拟

## Secrets
在 Airflow 运行期间，会使用包含特别敏感信息的变量或配置。本指南提供了保护这些数据的方法。延伸阅读：
### 静态加密
Airflow 使用Fernet对连接配置和变量配置中的密码进行加密。它保证使用它加密的密码在没有密钥的情况下无法被操纵或读取。
### 使用外部 Secret 存储
除了从环境变量或 Metastore 数据库中检索连接和变量之外，您还可以启用替代秘密后端以通过 Apache Airflow Community在 Secret backends中提供的后端检索 Airflow 连接或 Airflow 变量。
### 屏蔽敏感数据
当连接密码和敏感变量和密钥出现在任务日志、变量和 UI 的渲染字段视图中时，Airflow 默认会屏蔽连接的额外 (JSON) 字段中的连接密码和敏感变量和密钥。
* 敏感字段名称: 启用屏蔽后，Airflow 将始终屏蔽任务访问的每个连接的密码字段。默认屏蔽('access_token', 'api_key', 'apikey','authorization', 'passphrase', 'passwd', 'password', 'private_key', 'secret', 'token'). 此列表还可以扩展：
  ```
  [core]
  sensitive_var_conn_names = comma,separated,sensitive,names
  ```
* 添加自己的面具

## 报告漏洞
