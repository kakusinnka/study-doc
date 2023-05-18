# 发现
## GKE 概览
代管式 Kubernetes 服务 Google Kubernetes Engine (GKE)，借助该服务，您可以使用 Google 的基础架构大规模部署和运营容器化应用。  
### 何时使用 GKE
* GKE 的优势
* GKE 应用场景
### GKE 的工作原理
GKE 环境由节点组成，节点是 Compute Engine 虚拟机 (VM)，它们组合在一起构成集群。您将应用（也称为工作负载）打包到容器中。您可以将多个容器作为 Pod 部署到节点。您可以使用 Kubernetes API 与工作负载进行交互，包括管理、扩缩和监控。  
* Kubernetes 版本和功能
* 运营模式
### GKE 使用入门

## 选择 GKE 操作模式
GKE 为集群提供以下操作模式：
* Autopilot 模式（推荐）：GKE 管理底层基础架构，例如节点配置、自动扩缩、自动升级、基准安全配置和基准网络配置。
* 模式：您负责管理底层基础架构，包括配置各个节点。
### 为何选择 GKE Autopilot 模式
### 为何选择 GKE Standard 模式
### 价格差异
### 何时使用 Standard 而非 Autopilot

## 使用场景
### GKE上的数据

## GKE的插件
### Backup for GKE

# 开始
## 快速入门
### 部署容器化网络服务器应用
1. 启用 Artifact Registry API, Kubernetes Engine API .
2. 创建名为 hello-cluster 的 Autopilot 集群:
```
gcloud container clusters create-auto hello-cluster \
    --region=asia-northeast2
```
3. 获取用于集群的身份验证凭据:
```
gcloud container clusters get-credentials hello-cluster \
    --region asia-northeast2
```
4. 部署应用:
```
kubectl create deployment hello-server \
    --image=us-docker.pkg.dev/google-samples/containers/gke/hello-app:1.0
```
5. 公开 Deployment:
```
kubectl expose deployment hello-server --type LoadBalancer --port 80 --target-port 8080
```
6. 检查和查看应用
```
kubectl get pods
kubectl get service hello-server
http://EXTERNAL-IP 
```
7. 清理

删除应用的 Service:
```
kubectl delete service hello-server
```
 删除集群:
```
gcloud container clusters delete hello-cluster \
    --region asia-northeast2
```

### 部署特定语言的应用
