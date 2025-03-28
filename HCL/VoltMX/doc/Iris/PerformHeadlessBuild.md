## 执行 Headless 构建
无头构建是一种在不启动托管 Volt MX Iris 的 Eclipse 环境的情况下构建和发布应用程序的方法。相反，Ant 管理构建和发布过程。

执行 Headless 构建具有许多优势：
* 开发人员不必打开 Volt MX Iris 即可构建应用程序。这有助于将 Volt MX Iris 项目的编译和构建与 Cruise Control、Maven 和 Hudson 等持续构建和集成工具集成在一起。
* 非开发人员可以处理发布管理。
* 您可以指定要复制到所选特定位置的二进制文件，从而减少将文件复制到特定位置的手动工作。
* 您可以轻松地将应用程序部署到多个服务器。
* 您可以使用单个命令为多个平台构建应用程序。
* 您可以在启用二进制文件保护模式的情况下构建应用程序。
* 您需要配置一些其他设置才能使其正常工作。

运行 Headless 构建涉及以下任务：
