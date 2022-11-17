# 管理连接
Airflow 需要知道如何连接到您的环境。可以使用 UI 或环境变量创建和管理连接。

## 通过 UI 创建连接
打开 UI 的 Admin-> Connections 部分。 单击创建链接以创建新连接。

## 使用 UI 编辑连接
打开 UI 的 Admin-> Connections 部分。 单击连接列表中要编辑的连接旁边的铅笔图标。

## 从 CLI 创建连接
您可以通过 CLI 添加连接到数据库。

## 从 CLI 导出连接
您可以使用 CLI 从数据库导出连接。 支持的格式有 json、yaml 和 env。

## 在环境变量中存储连接
* 环境变量命名约定为 AIRFLOW_CONN_{CONN_ID}，全部大写。
* 使用环境变量设置的连接不会出现在 Airflow UI 中，但您可以在 DAG 文件中使用它们。

## 使用 .bashrc（或类似文件）
## 使用 docker .env
## 连接 URI 格式
## 生成连接 URI
## 编码任意 JSON
## 处理连接参数中的特殊字符
## 保护连接
## 测试连接
## 自定义连接类型