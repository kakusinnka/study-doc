# Build Native Local on Volt MX Iris

## 概述
Build Native Local 是 Volt MX Iris V9 中引入的一项功能，用于在 Volt MX Iris 中构建原生应用程序二进制文件，并将二进制文件存储在本地计算机上。

## 先决条件
以下是在 Volt MX Iris 中的本地计算机上构建本机应用程序的先决条件：
* 访问 Volt MX Foundry 环境。您必须使用 Volt MX Foundry Cloud 或本地环境的登录凭证登录 Volt MX Iris。
* 要发布到 Enterprise App Store，您必须具有 Volt MX Foundry V8 SP4 或更高版本。
* 配置各种 Project Settings。
* 特定于平台的先决条件：
  * 如果您选择为 iOS 平台构建应用程序，则必须提供开发方法、开发团队 ID 和 Keychain 密码。
  * 如果您选择为 Android 平台构建应用程序，则必须提供 Android Home 和 Java Home 的路径。
* 如果您选择在发布模式下为 Android 平台构建应用程序，则必须提供 Android 签名详细信息。
* 如果选择为 Windows 平台构建应用程序，则必须确保已在计算机上安装了“开发环境”，并在“项目设置”中提供 Windows 应用程序设置。 
* 如果您选择在保护模式下构建应用程序，则必须设置公钥和私钥。

## Post Build Actions 构建后操作
Volt MX Iris 中的 Build Native Local （构建本机本地） 选项为选定的本机平台构建应用程序，并执行选定的 Post Build 操作。在构建过程开始之前，您必须在 Build Native Local （构建本机本地） 窗口中选择 Post Build Action （构建后操作）。有三种类型的构建后操作：
* 生成本机应用程序 – 此操作会为您的本机应用程序生成二进制文件和构建日志，并将其保存在您的文件系统上
* 发布到我的 App Store – 此操作会将应用程序发布到您的企业 App Store
* 在我的设备上运行 – 此操作会将应用程序安装到您连接的设备上，并使您能够在设备上查看您的应用程序

### Generate Native App 生成本机应用程序
Generate Native App 操作会为您的 Native 应用程序生成二进制文件和构建日志，并将其保存在您的文件系统中。Iris 项目不必链接到 Volt MX Foundry 即可完成此操作。

### 发布到我的 App Store
Publish to my App Store 操作生成本机应用程序二进制文件并将应用程序发布到您的 Enterprise App Store。成功发布后，将显示一个确认窗口，该窗口共享一个链接，用于查看设备上的 Enterprise 应用商店。

### Run on my device 在我的设备上运行
Run on my Device （在我的设备上运行） 操作会将应用程序安装到连接的设备上，并使您能够在设备上查看您的应用程序。

## 在本地构建原生应用程序
从 Build Mode 下拉列表中，选择所需的构建模式。
* 调试模式 - 为了帮助您识别和修复错误，Volt MX Iris 会发出完整的符号调试信息。为了减少完成构建所需的时间，构建未针对代码执行进行优化，因此它的执行速度可能比针对发布优化的构建慢。此外，包含符号调试信息会导致最终可执行文件大于发布版本。
* 发布模式 - Volt MX Iris 优化构建以执行，需要更多时间来生成构建。它也不会发出完整的符号调试信息，从而使最终可执行文件比调试版本小。
* 保护模式 - 在 Volt MX Iris 中构建的应用程序可以通过在保护模式下构建应用程序来使用其他安全增强功能。
* 测试模式 - 为了帮助您识别和修复错误，Volt MX Iris 提供了在设备或仿真器上测试应用程序的功能。当您使用测试模式构建应用程序时，您可以利用 Volt MX Iris 的 Jasmine 测试框架来全面测试您的应用程序，并确保您的应用程序没有错误。您可以通过使用 Test 模式构建应用程序来运行 Jasmine 测试用例、测试套件和测试计划。