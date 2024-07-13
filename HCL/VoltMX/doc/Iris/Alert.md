# Alert Widget 警报小部件
“警报”小组件使您能够吸引用户的注意力，以通知某些内容或请求用户执行操作。

可以使用“警报”小组件的一些实际场景如下：
* 显示通知
* 显示广告
* 显示退出应用程序的确认
* 显示错误消息
* 显示提醒事项
* 使用户执行合规性任务，例如在允许用户使用应用程序之前完成待处理付款。

以下是“警报”小组件的一些功能：
* 模态：调用警报小组件时，用户无法在父应用程序上执行任何其他操作，而无需对警报执行某些操作。
* 处理“是”和“否”按钮：指定用户关闭警报时必须执行的 JavaScript 函数。您可以为“是”和“否”按钮提供此功能。
* 自定义警报：使用“警报”小组件自定义警报的外观、标题和图标。
* 警报是弹出消息的对话框。您可以使用以下类型的警报对话框：Confirmation 确认，Error 错误，Info 信息。

警报小组件功能大致可分为以下几类：
* Data Management 数据管理
* Enabling RTL 启用 RTL
* Miscellaneous 杂项

## Data Management 数据管理
* alertTitle：指定警报的标题。
* message 消息：指定要显示的警报的消息说明。

## Enabling RTL 启用 RTL
retainContentAlignment：有助于在应用 RTL 时保持小组件的内容对齐。
retainFlexPositionProperties：有助于在应用 RTL 时保留左、右和填充属性。
retainFlowHorizontalAlignment：使您能够将小组件的水平流从左向右更改。

## Miscellaneous 杂项
* dismissAlert：用于消除警报。
* alertHandler：指定通过“是”按钮或“否”按钮消除警报时应调用的 JavaScript 函数。
* accessibilityConfig 可访问性配置：使您能够控制小组件的辅助功能行为和替代文本。
* alertIcon：指定要显示的图标，以直观地指示警报的类型。
* alertType：指定要显示的警报窗口的类型。
* cursorType 游标类型：指定使用的鼠标指针的类型。
* noLabel 无标签：指定“否”标签的描述性文本。
* yesLabel 是标签：指定“是”标签的描述性文本。
* textOverflow 文本溢出：指定当文本消息超过图像高度时，是否在图像下方启用文本换行。

## Alert Widget Basics 警报小部件基础知识
### 何时使用警报
在许多情况下都可以使用警报，其中一些是：
1. 如果您想警告用户某些事情，例如，“您现在将被重定向到 xyz 网站，按”是“继续，按”否“取消”。
2. 发生错误，您想要通知用户。例如，如果用户输入了错误的密码。
3. 通知用户交易已成功完成。

### 使用构造函数创建警报：voltmx.ui.Alert
Example 例
```
var alert = voltmx.ui.Alert(basicConfigs, pspConfigs);
```
* basicConfigs 是具有配置属性的对象。
* pspConfigs(PSP: Platform-Specific Properties) 是具有特定于平台的配置属性的对象。