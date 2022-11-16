# Anthos 开发者沙盒
一个基于云的开发环境，可帮助您了解在 Anthos 上开发的感觉。

## 盒子里有什么东西？
* Cloud Shell - 预装了最好的 Google Cloud Platform 工具的计算环境。
* Cloud Code - 一个 IDE 扩展，可帮助您快速轻松地编写、运行和调试云原生应用程序。
* Minikube - 一种可以轻松在 Cloud Shell 中运行单节点 Kubernetes 集群的工具。
* Cloud Build Local Builder - 一种用于在本地运行持续集成过程的工具。

## 教程
本教程可让您深入了解 Anthos 开发实践，例如持续/迭代开发、本地构建和本地部署。

    在本教程结束时，您将拥有：
    1, 使用 minikube 在本地 Kubernetes 集群上运行此应用程序
    2, 使用 Cloud Build 本地构建器在本地运行测试
    3, 使用 Cloud Code 快速测试、调试和迭代更改
    4, 使用 Cloud Buildpacks 构建应用程序
    5, 将应用部署到 Cloud Run 本地模拟器

### 在本地集群中运行您的应用程序
    我们的示例应用程序已经可供您使用。 让我们在 minikube 上运行它，它是 Cloud Shell 中默认可用的本地 Kubernetes 集群，为您提供与部署到 Kubernetes 相同的体验，而无需基础设施：
    * 在您的终端中，运行以下命令：“minikube start -p cloud-run-dev-internal”
    * 如果出现提示，请授权 Cloud Shell 进行 Google Cloud API 调用
    * 在 Cloud Shell 中设置本地集群后，您将看到以下消息
      Done! kubectl is now configured to use "cloud-run-dev-internal" by default

<br/>

    现在让我们构建并运行这个应用程序：
    * 单击状态栏中的“ Cloud Code ”
    * 选择 “ Run on Kubernetes ”，确认您要使用“ cloud-run-dev-internal ”上下文
    * 几秒钟后将弹出一个输出面板，显示您的应用程序构建/部署的进度
    * 构建应用程序后（将需要几分钟），使用“输出”面板中显示的 Web 预览链接启动它，文本附近：Forwarded URL from service anthos-sandbox-sample-application-external:


恭喜！ 您刚刚使用 Cloud Code 在 Kubernetes 上运行了您的第一个应用程序。 下一步，让我们在本地运行我们的持续集成测试。

### 使用 Cloud Build 本地构建器在本地运行测试
现在让我们在本地为我们的应用程序运行测试。 我们将使用 Cloud Build 本地构建器 (cloud-build-local) 执行此操作，它允许我们在本地运行我们的持续集成套件将运行的完全相同的构建：

    * 在您的终端中，运行以下命令来运行测试 (test_application.py)。
    cloud-build-local --dryrun=false .
    注意：此命令会产生一些可以安全忽略的警告。
    * 你会看到测试失败了：
    ## FAIL: test_my_app (tests.test_application.TestMyApplication)

    Traceback (most recent call last): File
    "/workspace/tests/test_application.py", line 26, in test_my_app assert
    response.data == b"Hello Anthos" AssertionError

    ----------------------------------------------------------------------------

    Ran 1 test in 0.021s

    FAILED (failures=1)

看起来我们希望我们的应用程序说“Hello Anthos”而不是“Hello World”。 让我们在下一步中解决这个问题。

### 编辑和重新编译您的应用程序
Cloud Code 支持迭代开发，因此您部署的应用程序会在您编写代码时更新，无需在每次更改后重新部署。 我们的应用程序由以下部分组成：

    * 一个基本的 Web 应用程序 (main.py)，它返回“Hello, world!” 到所有收到的请求
    * 一个负载均衡器，“anthos-sandbox-sample-application-external”Kubernetes 服务 (hello.service.yaml)，它将我们的应用程序暴露给互联网。

要修改和自动重建我们的应用程序：

    * 将 main.py 更改为打印“Hello, Anthos!”。 文件会自动保存
    * 您会在“输出”面板中注意到您的应用程序自动开始重建
    * 应用完成构建和部署后，单击“输出”面板中的链接或返回打开的选项卡并刷新以查看更新的应用文本

### 使用 Cloud Buildpacks 构建应用程序
Google Cloud Buildpacks 允许您直接从源代码创建生产就绪的容器镜像，而无需使用 Dockerfile，随时可以部署在任何可以部署容器镜像的地方。

    首先，既然我们已经修复了错误，让我们重新运行测试：
    * 在您的终端中，从之前运行以下命令：cloud-build-local --dryrun=false .
    注意：此命令会产生一些可以安全忽略的警告。
    * 你会看到测试现在正在通过：Ran 1 test in 0.020s OK
    * 作为构建过程的一部分，cloud-build-local 工具还使用 Google Cloud Buildpacks 为您的应用程序生成容器映像。
    * 您可以通过输入以下命令并查看 LOCAL 输出下的详细信息来验证您的映像是否已构建：
      pack inspect-image anthos-sandbox-sample-application

### 将应用部署到 Cloud Run Emulator
现在我们已经使用 Cloud Buildpacks 构建了一个映像，我们可以选择将它直接部署到 Cloud Run，以利用它在流量增加时扩展的能力，并在不使用时扩展到零，从而消除任何闲置成本。

    通过在 Cloud Run Emulator 上本地重新部署我们的应用程序，我们可以获得与部署到 Cloud Run 相同的体验：
    * 从状态栏启动 Cloud Code
    * 选择在 Cloud Run Emulator 上运行
    * 现在将再次构建和部署您的应用
    * 部署应用程序后，使用输出面板中显示的链接启动它，靠近文本
      http://localhost:8080
      Update successful
    * 您可以通过单击按钮并选择“在端口 8080 上预览”来打开 Web 预览。