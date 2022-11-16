# 利用Cloud Shell Editor创建和部署容器化 Web 应用程序
了解如何使用 Cloud Code 创建和部署 Google Kubernetes Engine (GKE) 应用：

    1, 创建示例“Hello World”Kubernetes 应用程序
    2, 在本地 Kubernetes 集群上构建/测试此应用程序
    3, 编辑和调试 Kubernetes 应用
    4, 查看和浏览应用的日志
    5, 创建 GKE 集群
    6, 将应用部署到 GKE

## 创建您的网络应用程序
在本教程中，您将使用 Cloud Shell Editor 作为创建应用程序的环境。 编辑器预装了云开发所需的工具。

    1, 打开命令面板（可通过 Ctrl/Cmd+Shift+P 访问），然后运行 Cloud Code: New Application。
    2, 选择 Kubernetes 应用程序选项。
    3, 从示例 Kubernetes 应用程序列表中，选择 Go:Hello World。
    4, 为您的应用程序位置选择一个文件夹，然后单击创建新应用程序。
    5, Cloud Shell Editor 在新工作区中加载您的应用。 重新加载后，您的应用程序可以通过资源管理器视图访问。

## 在本地集群中测试您的应用
在 Cloud Shell 的本地 Kubernetes 集群中运行您的新应用：

    1, 在您的终端中，运行此命令【minikube start】以启动您的本地 minikube 集群。 这可能需要几分钟时间。
    2, 打开命令面板（可通过 Ctrl/Cmd+Shift+P 访问），然后运行 Cloud Code：Run on Kubernetes。
    3, 在 Cloud Shell 的本地 Kubernetes 集群中运行您的新应用, 确认您要使用 minikube 上下文。
    4, 如果出现提示，请授权 Cloud Shell 进行 Cloud API 调用。
    5, “输出”面板显示构建和部署应用程序的进度。
    6, 构建应用程序（这需要几分钟）后，您可以使用“输出”面板中显示的链接启动它。

## 编辑您的应用

    1, 修改您的 main.go 以打印“它已重新部署！” 。 文件会自动保存。
    2, 使用“输出”面板监控您的应用程序在重建时的进度。
    3, 在您的应用程序完成构建和部署后，通过单击“输出”面板中的链接来启动您的应用程序，或刷新您打开应用程序的选项卡以查看更新的应用程序。

## 查看应用日志
要在您的应用程序运行时对其进行分析：

    1, 通过键入 Cloud Code: View Logs using the Command Palette（可通过 Ctrl/Cmd+Shift+P 访问）启动日志查看器。
    2, 此视图允许您过滤和导航应用程序的日志。
    3, 指定部署或 Pod 过滤器以查看您的应用程序 go-hello-world 的日志。
    4, 在浏览器中刷新您的应用程序。
    5, 要在日志查看器中查看新生成的日志，请单击日志刷新按钮。

## 创建 GKE 集群
要创建新的 Google Kubernetes Engine (GKE) 集群以将您的应用程序部署到：

    1, 打开命令面板（可通过 Ctrl/Cmd+Shift+P 访问），然后运行 【Cloud Code: Create GKE Cluster】。
    2, 如果出现提示，请输入您的项目 ID。
    3, 如果您还没有项目，则需要创建一个新项目并启用计费才能完成此步骤。
    4, 如果需要，请通过单击启用 API 来启用您的 Compute 和 Kubernetes API。
    5, 如果出现提示，请单击 Google Kubernetes Engine。
    6, 选择创建 GKE 集群。
    7, 选择集群模式、集群所在的地区/区域（例如 us-east1-b）以及您选择的集群名称（例如 test-gke-cluster）。
    8, 单击创建集群。
    9, 创建集群需要几分钟时间。 创建集群后，它会列在 Kubernetes Explorer 视图中。

## 将您的应用部署到 GKE 集群

    1, 打开命令面板（可通过 Ctrl/Cmd+Shift+P 访问），然后运行 Cloud Code：Run on Kubernetes。
    2, 确认您新创建的集群作为您的应用程序的上下文。
    3, 确认您的映像注册表的默认选项。
    4, 成功部署应用程序后，您可以使用“输出”面板中显示的链接启动它。