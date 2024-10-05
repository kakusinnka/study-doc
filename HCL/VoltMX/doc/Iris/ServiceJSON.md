# JSON 适配器
通过 HTTP 协议使用 JSON 与外部数据源通信并以 JSON 格式返回响应的服务称为 JSON 服务

## 关于 JSON 适配器的概念
### Notations 符号
* JSON Object - {}
* JSON Array - []

### 重要考虑因素
* JSON 数组将由 JSON 对象数组或空数组组成。
* JSON Object 是一个键值对。键是 String，值可以是 String、number（int， float，double）、JSON Object 或 JSON Array。
* 下面有一些没有列举

### 选择元素
略

## 配置 JSON 端点适配器
要在 [Integration service definition](./IntegrationServiceDefinition.md) 选项卡中配置 JSON 服务，请执行以下步骤：