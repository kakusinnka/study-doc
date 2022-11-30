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
## Flower
## Kerberos
## Webserver
## Workload
## Secrets
## 报告