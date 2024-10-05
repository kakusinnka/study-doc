# 使用数据与服务面板功能
## Use Sample Services 使用示例服务
### 使用示例 Identity Service
操作演示，请看原文。

### 使用示例 Integration Service
操作演示，请看原文。

### 使用示例对象服务
操作演示，请看原文。

## Use Existing Services 使用现有服务
本节解释了如何使用数据与服务面板在您的应用程序中使用和配置现有的身份、集成和对象服务。

## 创建和使用新服务
本节解释了如何使用数据和服务面板创建新服务，以及如何在您的应用程序中使用这些服务。

### 创建 Identity Service
如果您的 Identity 服务类型是基本类型，则输入参数为 username 和 password。即使对于 OAuth 密码授予类型的服务，参数也是 username 和 password。对于所有其他类型的 OAuth 服务，没有输入参数。SAML Identity 服务遵循与 OAuth 服务类似的模式。

### 创建 Integration Service
默认情况下，您可以在数据与服务面板中查看集成服务。您还可以设置新的数据源。配置 Integration 服务后，您可以查看请求和响应参数。

### 创建对象服务
您可以在 Data & Services 面板中查看对象服务。您还可以设置新的数据源。配置对象服务后，您可以查看请求和响应参数。

### 创建后端工作流服务
您可以在数据和服务面板中查看后端工作流服务。使用 Workflow，您只需拖放不同类型的节点并根据您需要的逻辑连接它们，即可可视化和设计后端流程。

### 创建 Rules Service
您可以在数据和服务面板中查看规则服务。使用 Rules，您可以将业务逻辑定义并存储为一组规则，或存储为 Ruleset 的规则集合。

## 使用 Project Services
本节提供了有关如何从“数据和服务”面板发现和使用Project服务的信息。

### 使用 Identity Project Service
操作演示，请看原文。

### 使用对象项目服务
操作演示，请看原文。

### 使用后端工作流
操作演示，请看原文。

### 使用规则服务
操作演示，请看原文。

### 禁用/启用 Project Services 的分类
操作演示，请看原文。

### 取消服务关联
操作演示，请看原文。

### 编辑服务
操作演示，请看原文。

## 对象服务相关功能
您可以使用“数据与服务”面板执行以下与对象服务相关的操作：
* 为响应式 Web 生成 Object Services UI
* 为对象服务生成 CRUD 表单
* 为对象服务创建数据表
* 通过导入 Excel 文件配置对象数据模型
* 自定义数据模型对象的生成

### 为响应式 Web 生成 Object Services UI
当您将服务操作从数据与服务面板拖放到响应式Web表单上时，可以生成以下类型的表单：
* List and Details Using Response (for Get operations)
* Grid Using Response (for Get operations)
* Details Using Response (for Get operations)
* Entry (for Create and Update operations)

#### List and Details Using Response Form
下面的先不看了