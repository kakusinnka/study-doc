# 创建集群
## 使用 Minikube 创建集群
Kubernetes 是一个生产级别的开源平台，可协调在计算机集群内和跨计算机集群的应用容器的部署（调度）和执行.  
Kubernetes 协调一个高可用计算机集群，每个计算机作为独立单元互相连接工作。Kubernetes 以更高效的方式跨集群自动分发和调度应用容器。  
一个 Kubernetes 集群包含两种类型的资源:
* Master 调度整个集群
* Nodes 负责运行应用  
![集群图](../../images/k8s_cluster.svg)  
Master 负责管理整个集群。  
Node 是一个虚拟机或者物理机，它在 Kubernetes 集群中充当工作机器的角色  
Node 使用 Master 暴露的 Kubernetes API 与 Master 通信。
## 交互式教程 - 创建集群
```
minikube version
minikube start
kubectl version
kubectl cluster-info
```

# 部署应用
## 使用 kubectl 创建 Deployment
Deployment 负责创建和更新应用程序的实例  
应用程序需要打包成一种受支持的容器格式，以便部署在 Kubernetes 上  
![集群图](../../images/k8s-module_02_first_app.svg)  

## 交互式教程 - 部署应用
```
kubectl version
kubectl get nodes
kubectl create deployment kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1
kubectl get deployments

# 第二个终端运行
kubectl proxy

curl http://localhost:8001/version
export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.etadata.name}}{{"\n"}}{{end}}')
echo Name of the Pod: $POD_NAME
curl http://localhost:8001/api/v1/namespaces/default/pods/$POD_NAME/
```

# 了解你的应用
## 查看 pod 和工作节点
### Kubernetes Pods
Pod 是 Kubernetes 抽象出来的，表示一组一个或多个应用程序容器（如 Docker），以及这些容器的一些共享资源。
![Pod 概览](../../images/k8s-module_03_pods.svg)  
### 工作节点
一个 pod 总是运行在工作节点。工作节点是 Kubernetes 中的参与计算的机器，可以是虚拟机或物理计算机，具体取决于集群。每个工作节点由主节点管理。工作节点可以有多个 pod ，Kubernetes 主节点会自动处理在集群中的工作节点上调度 pod 。 主节点的自动调度考量了每个工作节点上的可用资源。  
每个 Kubernetes 工作节点至少运行:
* Kubelet，负责 Kubernetes 主节点和工作节点之间通信的过程; 它管理 Pod 和机器上运行的容器。
* 容器运行时（如 Docker）负责从仓库中提取容器镜像，解压缩容器以及运行应用程序。
![工作节点概览](../../images/k8s-module_03_nodes.svg)  

## 交互式教程-了解你的应用
```
# 查找现有的 Pod
kubectl get pods
# 获取有关 Pod 的详细信息
kubectl describe pods
# 打开一个新终端并运行代理
kubectl proxy
# 获取 Pod 名称并将其存储在 POD_NAME 环境变量中
export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')
echo Name of the Pod: $POD_NAME
# 要查看我们的应用程序的输出，请运行 curl 请求
curl http://localhost:8001/api/v1/namespaces/default/pods/$POD_NAME/proxy/
# 应用程序通常发送到 STDOUT 的任何内容都会成为 Pod 中容器的日志。 我们可以使用 kubectl logs 命令检索这些日志
kubectl logs $POD_NAME
# 使用 exec 命令并将 Pod 的名称用作参数
# 列出环境变量：
kubectl exec $POD_NAME -- env
# 在 Pod 的容器中启动一个 bash 会话
kubectl exec -ti $POD_NAME -- bash
# 要关闭您的容器连接，请运行:
exit
```

# 公开地暴露你的应用
## 使用 Service 暴露你的应用
## 交互式教程 - 暴露你的应用

# 缩放你的应用
# 更新你的应用