# Widget 程序员指南
Volt MX Iris 是一个功能强大且易于使用的集成开发环境 （IDE），用于为多个平台开发、构建、测试、调试和部署移动应用程序 - 所有这些都来自单个代码库。

Volt MX Iris 允许您通过从 Widget Library 中拖动小部件并将它们拖放到表单或其他容器对象上来直观地创建应用程序，从而快速创建移动应用程序的用户界面。这些小组件具有可以在 Volt MX Iris 中设置的属性，也可以通过您作为应用程序的一部分编写的代码进行设置和修改。

Volt MX Iris Widget 程序员指南介绍了每个小部件及其属性，以及如何编写 JavaScript 代码来更改属性并控制应用程序中小部件的行为。

## Widgets Overviews 小部件概述
小部件是 Volt MX Iris 中的可视化组件，用于快速构建应用程序用户界面，并使用最少的自定义代码。尽管大多数小组件属性都可以使用 Volt MX Iris IDE 进行设置，但某些属性需要通过自定义 JavaScript 代码进行设置和管理。本指南介绍了如何完成此操作，并列出了将用于与 Volt MX Iris 小部件交互的属性和事件。

小组件是一小块可重用的代码，其中包括图形用户界面元素，这些元素可根据移动设备目标的功率和分辨率进行优雅缩放。一些小部件用作容器来容纳其他小部件。

VoltMXwidgets 还包括对平台特定属性的支持。这些特定于平台的属性允许你的应用在每个平台上具有原生外观。

根据小组件的行为和特征，小组件分为容器、基本和高级。
* 基本小部件：这些小部件用于表单上的基本功能。它们是应用程序设计中最常用的小部件。这些小组件是独立于容器小组件运行的组件。
* 容器小部件：这些小部件包含容器、基本或高级小部件。
* 高级小部件：用于在应用程序中实现高级交互。您可以将这些小部件与基本小部件一起使用，以实现复杂的交互设计。

## Widgets List 小部件列表
* [Alert](./Alert.md) 警报: 一个预配置的对话框，弹出一个消息，如确认或错误。

## App Menu 应用菜单
[App Menu](./AppMenu.md) 应用菜单：通常显示在应用程序表单底部的菜单栏。

## ARRenderer
[ARRenderer](./ARRenderer.md) 帮助您在应用中实现增强现实。

## Browser 浏览器
[Browser](./Browser.md) 在应用程序上下文中显示 HTML 内容，而无需离开应用程序或从应用程序打开本机浏览器

## Button 按钮
[Button](./Button.md) 矩形或圆角矩形，中心带有描述性标题。使用按钮触发操作，例如导航到窗体或与对话框交互。

## Calendar 日历
[Calendar](./Calendar.md) 向用户显示日历，以便用户可以选择一个或多个日期。

## Camera 照相机
[Camera](./Camera.md) 控制设备上的摄像头进行拍照和录像。

## CheckBoxGroup
[CheckBoxGroup](./CheckBoxGroup.md) 显示一组相关复选框，以便用户可以从组中选择一个或多个项目。

## ComboBox 组合盒
[ComboBox](./ComboBox.md) 向用户显示一个下拉列表，允许他们选择单个项目

## CordovaBrowser 科尔多瓦浏览器
在应用程序中显示 HTML 内容，而无需离开应用程序或打开本机浏览器。使用 [CordovaBrowser](./Cordova.md) 小组件将您的 Web 或 Apache Cordova （PhoneGap） 应用程序移植到 Volt MX Iris。

## DataGrid 数据网格
[DataGrid](./DataGrid.md) 数据网格：向用户显示数据的表格视图。

## FlexContainer
允许您按水平、垂直或自由形式的顺序排列多个小部件。您只能将 [FlexContainer](./FlexContainer.md) 添加到 Flex 表单中。

## FlexForm 弹性表格
[FlexForm](./FlexForm.md) 是最顶层的容器小部件，您可以在其上放置任意数量的小部件，在表单之间导航是构建应用程序功能的常用方法。

## FlexScrollContainer
[FlexScrollContainer](./FlexScrollContainer.md) 可滚动的 UI 容器窗体，允许在列表中显示的项目多于屏幕大小允许的项目。

## Image 图像
[Image](./Image2.md) 显示 PNG 文件中的图形（本地或远程）。

## Label 标签
[Label](./Label.md) 在窗体上显示不可编辑的文本。

## ListBox 列表框
[ListBox](./ListBox.md) 向用户显示下拉列表，并使用户能够选择一个或多个项目。

## 略