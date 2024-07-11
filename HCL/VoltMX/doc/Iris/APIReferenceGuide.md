# Volt MX Iris
Volt MX Iris 是一个功能强大且易于使用的集成开发环境 （IDE），用于为多个平台开发、构建、测试、调试和部署移动应用程序 （应用程序），所有这些都来自单个代码库。Volt MX Iris 使您能够快速开发移动应用程序，同时让您能够根据需要灵活地与后端服务集成。此外，您还可以将最好的原生、Web 和混合环境集成到您的应用程序中。

Volt MX Iris API 包含一组 API，您可以在使用 Volt MX Iris 编写的应用程序中使用这些 API。这些 API 使您能够执行诸如对表执行各种操作、操作字符串或调用服务等任务。Volt MX Iris API 库由以下内容组成：  
* 加速度计 API(Accelerometer API)：加速度计 API 允许您捕获 X、Y、Z 方向上的设备运动加速度，并提供开箱即用的机制来注册抖动手势事件。
* 适用于 iOS 的操作表 API(Action Sheet API for iOS)：操作表 API 为 iOS 应用上的 Apple 操作表提供支持。
* 警报 API(Alert API)：voltmx.ui 命名空间包含一个函数，该函数使应用能够弹出警报对话框，以向应用用户显示重要消息。
* 动画 API(Animation API)：动画 API 函数可帮助应用将动画添加到 SegmentedUI 小组件的行中。
* 适用于 iOS 的应用扩展 API(App Extension API for iOS)：Volt MX Iris API 为 iOS 应用中的应用扩展提供支持。
* 应用组 API(App Group API)：应用组 API 包含应用可用于在 iOS 上共享数据的函数。
* 应用程序 API(Application API)：在应用程序的生命周期中，移动设备通常会触发多个事件。本章中的 API 允许您侦听这些事件，并使用特定于应用程序的功能覆盖它们。本章包含命名空间为 voltmx.application 的所有 API。
* 应用程序设置 API(Application Settings API)：应用程序设置 API 使应用能够控制应用程序级别设置，以便应用程序的最终用户可以在 iOS 上修改配置和更改应用程序行为。
* 后台代理 API(Background Agent API)：后台代理 API 使 Windows 应用能够在后台执行代码。
* 锁屏提醒 API(Badge API)：您的应用使用锁屏提醒 API 显示 iOS 应用的图标锁屏提醒。
* 电池 API(Battery API)：电池 API 提供了一个标准接口，可用于多个硬件平台，用于检查设备电池的当前状态。
* 信标 API(Beacon API)：信标 API 使您的应用能够使用 iOS 信标。
* 书签和刷新 API(Bookmark and Refresh API)：书签和刷新 API 使开发人员能够向 URL 添加上下文，以便在最终用户为其添加书签或共享时，URL 携带必要的参数，以便相应地呈现应用程序。
* 相机 API(Camera API)：相机 API 可帮助您的应用管理相机小组件捕获的数据。
* 超级按钮设置 API(Charm Setting API)：超级按钮设置 API 使你的应用能够访问和使用 Windows 超级按钮。
* 客户端身份验证 API(Client Authentication API)：客户端身份验证 API 使应用能够对想要访问 HTTPS 服务器的客户端进行身份验证。
* 加密 API(Cryptography API)：加密是保护信息的过程。它可以定义为将数据转换为加扰文本（隐藏其可读性和含义）并使用密钥对其进行破译。这些数据可以通过公共和专用网络安全地发送。本章包含所有具有命名空间 voltmx.crypto 的 API。
* ForceTouch API：ForceTouch API 提供支持 3D Touch 功能的功能。
* 功能模块 API(Functional Modules API)：功能模块 API 使应用能够将功能模块加载到应用中。
* 地理位置 API(Geolocation API)：GeoLocation API 定义了位置信息（例如与移动设备关联的纬度和经度）的高级接口。
* 手势 API(Gesture API)：手势 API 使应用能够访问移动设备的底层手势读取功能。
* 图像 API(Image API)：图像 API 为应用提供图像处理工具。
* 输入和输出 API(Input and Output API)：使用输入和输出 API 访问设备的底层文件系统。
* 国际化 API(Internationalization API)：i18n API 使您能够以支持各种语言和地区的方式设计或开发应用程序。国际化的命名空间是 voltmx.i18n。
* 本地身份验证 API(Local Authentication API)：voltmx.localAuthentication 命名空间包含使应用能够执行 Touch ID 生物识别指纹识别的函数。
* 语言 API(Language API)：语言 API 是针对未使用 try/catch 块处理的异常实现的。
* 动态磁贴 API(Live Tiles API)：动态磁贴使你能够在设备的“开始”屏幕上将应用程序表示为磁贴。您可以使用动态磁贴启动应用程序。本章包含所有可用于添加动态磁贴的 API。本章中所有 API 的命名空间都是 voltmx.application。
* 地图 API(Map API)：voltmx.map 命名空间提供与地图小组件结合使用的常量和函数。
* Math API：Math API 具有可用于执行数学运算的函数。
* 媒体 API(Media API)：媒体 API 使应用能够播放和录制音频文件。
* 原生函数 API(Native Function API)：Volt MX Iris 提供原生函数 API，允许您在 Volt MX Iris 中使用 iOS 和 Android 平台的原生函数。通过 JavaScript API 提供对本机函数的访问。
* 网络(Network)：网络 API 使您能够调用服务调用或取消网络调用。本章包含命名空间 voltmx.net 的所有 API。
* 通知 API(Notifications API)：通知系统允许用户随时了解应用中的相关和及时事件。
* 离线数据访问 API(Offline Data Access API)：此 API 允许您将数据永久存储到设备数据存储中。
* 操作系统 API(Operating System API)：本章包含命名空间为 voltmx.os 的所有 API。
* Passbook API：Passbook API 用于将航空公司登机牌、电影票和礼品卡等物品保存在一个地方。
* Phone API：通过该接口中的函数，您可以在移动设备上访问底层平台的默认应用程序并执行操作。Phone API 的命名空间为 voltmx.phone。
* 运行时权限 API(Runtime Permission API)：使用此 API 中的函数，您的应用可以在运行时获取权限。
* 标准 Volt MX API(Standard Volt MX API)：具有命名空间 voltmx 的泛型函数。
* 字符串 API(String API)：字符串库具有可用于操作字符串的 API。命名空间为 voltmx.string。
* 主题 API(Theme API)：主题 API 允许您为处于不同状态的小部件指定通用外观。
* 线程 API(Threading API)：线程 API 可帮助 JavaScript 绑定在主线程上工作。
* Timer API：Timer API 函数使您能够定期计划功能块的执行。Timer API 的命名空间是 voltmx.timer。
* Toast API：Toast API 在 Volt MX Iris 应用中实现 Toast 消息。
* 工作线程 API(Worker Thread API)：工作线程 API 中的函数为应用提供了一种方法，用于在多个并行执行上下文中以并发方式执行不同的任务。
* 在 Android 中与其他应用程序共享文件：Android，从一个应用程序与另一个应用程序共享文件以内容 URI 的形式发生。因此，您必须让您的应用生成要与其他应用共享的文件的内容 URI。