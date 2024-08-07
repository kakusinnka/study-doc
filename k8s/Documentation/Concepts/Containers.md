## 镜像
### 镜像名称
### 更新镜像
#### 镜像拉取策略
Kubernetes中的容器镜像拉取策略定义了何时和如何拉取容器镜像。当创建或更新容器时，Kubernetes将根据指定的拉取策略拉取镜像。  
Kubernetes提供了以下几种镜像拉取策略：
1. Always: 总是拉取最新的镜像。如果在运行中发现了新的镜像，则用最新的镜像替换现有的镜像。如果镜像标签被更改为新的标签，也会拉取新的镜像。
2. IfNotPresent: 如果本地存在相应的镜像，则使用本地镜像。否则，从容器镜像仓库中拉取新的镜像。
3. Never: 只使用本地镜像，不会拉取远程镜像。如果本地不存在该镜像，则启动容器失败。
#### ImagePullBackOff 
ImagePullBackOff 是一个 Pod 状态，表示 Pod 失败了因为容器镜像无法拉取。这通常是因为容器镜像在指定的 registry 中不存在或无法访问，或者是因为访问凭证不正确。
### 带镜像索引的多架构镜像
### 使用私有仓库
#### 配置 Node 对私有仓库认证
#### config.json 说明
#### 提前拉取镜像
#### 在 Pod 上指定 ImagePullSecrets
### 使用案例

## 容器环境
### 容器环境
Kubernetes 容器环境为容器提供了几个重要的资源：
* 文件系统，它是镜像和一个或多个卷的组合。
* 有关容器本身的信息。
* 有关集群中其他对象的信息。
### 容器信息
### 集群信息

## 容器运行时类（Runtime Class）


## 容器生命周期回调