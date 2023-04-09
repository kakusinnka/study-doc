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
### Kubernetes Service 总览
Kubernetes 中的服务(Service)是一种抽象概念，它定义了 Pod 的逻辑集和访问 Pod 的协议。尽管每个 Pod 都有一个唯一的 IP 地址，但是如果没有 Service ，这些 IP 不会暴露在集群外部。Service 允许你的应用程序接收流量。
### Service 和 Label
![Service](../../images/k8s-module_04_services.svg)  
Service 通过一组 Pod 路由通信。Service 是一种抽象，它允许 Pod 死亡并在 Kubernetes 中复制，而不会影响应用程序。在依赖的 Pod (如应用程序中的前端和后端组件)之间进行发现和路由是由Kubernetes Service 处理的。

---
---

![Label](../../images/k8s-module_04_labels.svg)  
Service 匹配一组 Pod 是使用 标签(Label)和选择器(Selector), 它们是允许对 Kubernetes 中的对象进行逻辑操作的一种分组原语。标签(Label)可以在创建时或之后附加到对象上。他们可以随时被修改。

## 交互式教程 - 暴露你的应用
```
# 步骤 1 创建一个新服务
# 查找现有的 Pod
kubectl get pods
# 列出集群中的当前服务
kubectl get services
# 创建新服务并将其暴露给外部流量，我们将使用带有 NodePort 作为参数的 expose 命令
kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080
# 要找出外部打开的端口（通过 NodePort 选项），我们将运行
kubectl describe services/kubernetes-bootcamp
---
Name:                     kubernetes-bootcamp
Namespace:                default
Labels:                   app=kubernetes-bootcamp
Annotations:              <none>
Selector:                 app=kubernetes-bootcamp
Type:                     NodePort
IP Families:              <none>
IP:                       10.106.150.184
IPs:                      10.106.150.184
Port:                     <unset>  8080/TCP
TargetPort:               8080/TCP
NodePort:                 <unset>  30778/TCP
Endpoints:                172.18.0.4:8080
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>
---
# 创建一个名为 NODE_PORT 的环境变量，该变量具有分配的节点端口值
export NODE_PORT=$(kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}')
# 现在我们可以使用 curl、节点的 IP 和对外暴露的端口来测试应用程序是否暴露在集群之外
curl $(minikube ip):$NODE_PORT

# 第 2 步：使用标签
# 使用 describe deployment 命令，您可以看到标签的名称
kubectl describe deployment
---
Name:                   kubernetes-bootcamp
Namespace:              default
CreationTimestamp:      Sun, 09 Apr 2023 01:47:38 +0000
Labels:                 app=kubernetes-bootcamp
Annotations:            deployment.kubernetes.io/revision: 1
Selector:               app=kubernetes-bootcamp
Replicas:               1 desired | 1 updated | 1 total | 1 available | 0 unavailable
StrategyType:           RollingUpdate
MinReadySeconds:        0
RollingUpdateStrategy:  25% max unavailable, 25% max surge
Pod Template:
  Labels:  app=kubernetes-bootcamp
  Containers:
   kubernetes-bootcamp:
    Image:        gcr.io/google-samples/kubernetes-bootcamp:v1
    Port:         8080/TCP
    Host Port:    0/TCP
    Environment:  <none>
    Mounts:       <none>
  Volumes:        <none>
Conditions:
  Type           Status  Reason
  ----           ------  ------
  Available      True    MinimumReplicasAvailable
  Progressing    True    NewReplicaSetAvailable
OldReplicaSets:  <none>
NewReplicaSet:   kubernetes-bootcamp-fb5c67579 (1/1 replicas created)
Events:
  Type    Reason             Age   From                   Message
  ----    ------             ----  ----                   -------
  Normal  ScalingReplicaSet  18m   deployment-controller  Scaled up replica set kubernetes-bootcamp-fb5c67579 to 1
---
# 我们将使用带有 -l 作为参数的 kubectl get pods 命令，后跟标签值
kubectl get pods -l app=kubernetes-bootcamp
# 您可以执行相同的操作来列出现有服务
kubectl get services -l app=kubernetes-bootcamp
# 要应用新标签，我们使用 label 命令，后跟对象类型、对象名称和新标签
# 获取 Pod 的名称并将其存储在 POD_NAME 环境变量中
export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')
# 要应用新标签，我们使用 label 命令，后跟对象类型、对象名称和新标签
kubectl label pods $POD_NAME version=v1
# 这将为我们的 Pod 应用一个新标签（我们将应用程序版本固定到 Pod），我们可以使用 describe pod 命令检查它
kubectl describe pods $POD_NAME
# 我们现在可以使用新标签查询 pod 列表
kubectl get pods -l version=v1

# 步骤 3 删除服务
# 要删除服务，您可以使用删除服务命令。 标签也可以在这里使用：
kubectl delete service -l app=kubernetes-bootcamp
# 确认服务已经消失：
kubectl get services
# 这确认我们的服务已被删除。 要确认路由不再暴露
curl $(minikube ip):$NODE_PORT
# 您可以通过 pod 内的 curl 确认该应用程序仍在运行：
kubectl exec -ti $POD_NAME -- curl localhost:8080
```

# 缩放你的应用
## 运行应用程序的多个实例
### 扩缩概述
扩缩 是通过改变 Deployment 中的副本数量来实现的。

## 交互教程 - 缩放你的应用
此交互式场景的目标是使用 kubectl scale 扩展部署并查看负载均衡的运行情况
```
# 第 1 步：扩展部署
# 要列出您的部署
kubectl get deployments
# 查看 Deployment 创建的 ReplicaSet
kubectl get rs
# 使用 kubectl scale 命令扩展副本，参数依次为：部署类型、名称和所需的实例数
kubectl scale deployments/kubernetes-bootcamp --replicas=4
# 要再次列出您的 Deployments
kubectl get deployments
# 检查 Pod 的数量是否发生了变化
kubectl get pods -o wide
# 更改已在部署事件日志中注册。 要检查这一点，请使用 describe 命令
kubectl describe deployments/kubernetes-bootcamp

# 第 2 步：负载平衡
# 找出暴露的 IP 和 port
kubectl describe services/kubernetes-bootcamp
# 创建一个名为 NODE_PORT 的环境变量，其值为节点端口
export NODE_PORT=$(kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}')
# 接下来，我们将 curl 暴露的 IP 和 port。 多次执行命令:我们会针对每个请求访问不同的 Pod。 这表明负载平衡正在工作。
curl $(minikube ip):$NODE_PORT

# 第 3 步：缩小规模
# 要将服务缩减为 2 个副本，请再次运行 scale 命令：
kubectl scale deployments/kubernetes-bootcamp --replicas=2
# 列出 Deployments 以检查是否使用 get deployments 命令应用了更改：
kubectl get deployments
# 检查 Pod 的数量是否发生了变化，确认 2 个 Pod 已终止。
kubectl get pods -o wide
```
# 更新你的应用
## 执行滚动更新
### 更新应用程序
### 滚动更新概述
滚动更新允许通过使用新的实例逐步更新 Pod 实例从而实现 Deployments 更新，停机时间为零。  
![滚动更新](../../images/module_06_rollingupdates2.svg)  

## 交互式教程 - 更新你的应用
此场景的目标是使用 kubectl set image 更新已部署的应用程序并使用 rollout undo 命令回滚。
```
# 第一步：更新应用程序版本
# 要列出您的部署，请运行获取部署命令：
kubectl get deployments
# 列出正在运行的 Pod
kubectl get pods -o wide
# 要查看应用程序的当前映像版本，请运行 describe pods 命令并查找 Image 字段
kubectl describe pods
# 要将应用程序的映像更新到版本 2，请使用 set image 命令，后跟部署名称和新映像版本
kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=jocatalin/kubernetes-bootcamp:v2

# 第 2 步：验证更新
首先，检查应用程序是否正在运行。 要查找暴露的 IP 和 port，请运行 describe service 命令
kubectl describe services/kubernetes-bootcamp
# 创建一个名为 NODE_PORT 的环境变量，该变量具有分配的节点端口值
export NODE_PORT=$(kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}')
# 对暴露的 IP 和 port 执行 curl
curl $(minikube ip):$NODE_PORT
# 您还可以通过运行 rollout status 命令来确认更新的实时状态
kubectl rollout status deployments/kubernetes-bootcamp
# 要查看应用程序的当前图像版本，请运行 describe pods 命令
kubectl describe pods

# 第 3 步：回滚更新
# 让我们执行另一个更新，并部署一个标记为 v10 的镜像
kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=gcr.io/google-samples/kubernetes-bootcamp:v10
# 使用 get deployments 查看部署状态
kubectl get deployments
# 运行 get pods 命令以列出所有 Pod
kubectl get pods
# 要更深入地了解问题，请运行 describe pods 命令.在受影响的 Pod 输出的事件部分，请注意存储库中不存在 v10 映像版本。
kubectl describe pods/kubernetes-bootcamp-59b7598c77-7xh96
# 要将部署回滚到上一个工作版本，请使用 rollout undo 命令
kubectl rollout undo deployments/kubernetes-bootcamp
```