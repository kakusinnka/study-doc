# 你好，Minikube
本教程向你展示如何使用 Minikube 在 Kubernetes 上运行一个应用示例。
## 教程目标
* 将一个示例应用部署到 Minikube。
* 运行应用程序。
* 查看应用日志。
## 准备开始
* 安装 [kubectl](https://kubernetes.io/zh-cn/docs/tasks/tools/#kubectl)
* 安装 [Minikube](https://minikube.sigs.k8s.io/docs/start/)
## 创建 Minikube 集群
```
minikube start
```
## 打开仪表板
```
minikube dashboard
```
## 创建一个 Deployment
```
# 使用 kubectl create 命令创建管理 Pod 的 Deployment。
kubectl create deployment hello-node --image=registry.k8s.io/e2e-test-images/agnhost:2.39 -- /agnhost netexec --http-port=8080

# 查看 Deployment
kubectl get deployments

# 查看 Pod
kubectl get pods

# 查看集群事件
kubectl get events

# 查看 kubectl 配置
kubectl config view
```
## 创建一个 Service
```
# 使用 kubectl expose 命令将 Pod 暴露给公网
kubectl expose deployment hello-node --type=LoadBalancer --port=8080

# 查看 Service
kubectl get services

# 
minikube service hello-node
```
## 启用插件
```
# 列出当前支持的插件
minikube addons list

# 启用插件，例如 metrics-server
minikube addons enable metrics-server

# 查看通过安装该插件所创建的 Pod 和 Service
kubectl get pod,svc -n kube-system

# 禁用 metrics-server
minikube addons disable metrics-server
```
## 清理
```
# 现在可以清理你在集群中创建的资源：
kubectl delete service hello-node
kubectl delete deployment hello-node

# 停止 Minikube 集群
minikube stop
```