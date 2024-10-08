# Cordova Browser Cordova 浏览器
使用 Cordova 浏览器小组件在应用程序中显示基于 Cordova 的 HTML 内容。HTML 内容可以是静态的，也可以是从 URL 获取的。

## 重要考虑因素
* 对于 iOS 平台，请将 Cordova 浏览器小组件用作屏幕级小组件，并将其他小组件移动到页眉或页脚。否则，可能会显示双滚动条。
* Cordova 浏览器小部件是内存和性能密集型的。初始 RAM 使用率很高，并且 RAM 使用率与渲染图像和静态文本的大小和数量成正比。
* 如果同一应用程序中有多个 Cordova 浏览器小部件实例，则信息共享（例如，Cookie）可能无法按预期运行。不要在一个窗体上放置多个 Cordova 浏览器小部件，也不要在一个应用程序中放置两个以上的 Cordova 浏览器小部件。
* 不要使用 Cordova 浏览器小组件来显示富文本。它只能用于显示大型 HTML 内容。使用 RichText 小组件显示富文本。
* 避免使用 Cordova 浏览器小组件创建外观和行为类似于 Web 浏览器的应用程序。通常，用户希望使用本机浏览器浏览 Web 内容。

## Look Properties Look 属性
略

## Cordova 浏览器属性
### Master Data 主数据
* 内容。显示一个文本字段，您可以在其中输入或粘贴要显示的 HTML 内容。
* 网址。显示一个文本框，您可以在其中指定要显示的 HTML 页的 URL。URL 必须以 http:// 开头。
* 本地文件。显示一个文本框，您可以在其中指定用于启动本地 HTML 内容（如 Web 应用程序）的基于 Web 的本地文件。

### Detect Phone Number 检测电话号码
指定“Cordova 浏览器”小组件是否支持检测网页上的电话号码，并将其显示为可单击的链接。当用户单击电话链接时，电话应用程序将启动并拨打该号码。

### Native Communication 本地通信
指定是否允许在 Cordova 浏览器小组件中运行的 Web 应用 JavaScript 模块在 Volt MX 本机上下文中执行 JavaScript 代码。

### Zoom 缩放
指定是否启用 Cordova 浏览器构件的缩放功能。缩放功能提供了更改视图区域比例的功能。

### Base URL 基本 URL
对于 iOS 平台，指定 URL 以提供其他基于 Web 的功能。

### Enable Cache 启用缓存
对于 Windows 8 平台，指定是否相对于 Cordova 浏览器小组件缓存数据。

## Actions 行动
* onFailure：当指定的主数据 URL 无法加载内容时触发该操作。
* onSuccess：当指定的主数据 URL 成功加载内容时，将触发该操作。
* onTouchStart：当用户触摸触摸表面时触发操作。此事件以异步方式发生。
* onTouchMove：当触摸在触摸表面上连续移动直到移动结束时，将触发该操作。此事件以异步方式发生。
* onTouchEnd：当用户触摸从触摸表面释放时触发操作。此事件以异步方式发生。