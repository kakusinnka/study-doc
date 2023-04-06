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

## 交互式教程-了解你的应用


# 公开地暴露你的应用
# 缩放你的应用
# 更新你的应用