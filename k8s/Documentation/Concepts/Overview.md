## 概述
Kubernetes 是一个可移植、可扩展的开源平台，用于管理容器化的工作负载和服务，方便进行声明式配置和自动化。Kubernetes 拥有一个庞大且快速增长的生态系统，其服务、支持和工具的使用范围广泛。
### 时光回溯
![容器技术](../../images/container_evolution.svg)
### 为什么需要 Kubernetes，它能做什么？
Kubernetes 为你提供了一个可弹性运行分布式系统的框架。 Kubernetes 会满足你的扩展要求、故障转移你的应用、提供部署模式等。  
Kubernetes 为你提供：
* 服务发现和负载均衡
* 存储编排
* 自动部署和回滚
* 自动完成装箱计算
* 自我修复
* 密钥与配置管理
### Kubernetes 不是什么
Kubernetes 不是传统的、包罗万象的 PaaS（平台即服务）系统。 由于 Kubernetes 是在容器级别运行，而非在硬件级别，它提供了 PaaS 产品共有的一些普遍适用的功能， 例如部署、扩展、负载均衡，允许用户集成他们的日志记录、监控和警报方案。 但是，Kubernetes 不是单体式（monolithic）系统，那些默认解决方案都是可选、可插拔的。 Kubernetes 为构建开发人员平台提供了基础，但是在重要的地方保留了用户选择权，能有更高的灵活性。  
此外，Kubernetes 不仅仅是一个编排系统，实际上它消除了编排的需要。 编排的技术定义是执行已定义的工作流程：首先执行 A，然后执行 B，再执行 C。 而 Kubernetes 包含了一组独立可组合的控制过程，可以持续地将当前状态驱动到所提供的预期状态。 你不需要在乎如何从 A 移动到 C，也不需要集中控制，这使得系统更易于使用且功能更强大、 系统更健壮，更为弹性和可扩展。
### Kubernetes 组件
当您部署 Kubernetes 时，您会得到一个集群。  
Kubernetes 集群由一组运行容器化应用程序的工作机器（称为节点）组成。 每个集群至少有一个工作节点。  
工作节点托管作为应用程序工作负载组件的 Pod。 控制平面管理集群中的工作节点和 Pod。 在生产环境中，控制平面通常运行在多台计算机上，一个集群通常运行多个节点，提供容错和高可用性。
![Kubernetes 组件](../../images/k8s-components.png)
#### 控制平面组件（Control Plane Components） 保安室
控制平面的组件做出关于集群的全局决策（例如，调度），以及检测和响应集群事件（例如，当部署的副本字段不满足时启动新的 pod）。
#### kube-apiserver 保安本人
Kube-apiserver 是 Kubernetes 的核心组件之一，是控制平面的关键组件之一，为用户和管理员提供了与 Kubernetes 集群进行交互的途径。
#### etcd 工作记录本
etcd是Kubernetes的核心组件之一，它是一个可靠、高效、分布式的键值存储系统，用于存储Kubernetes集群的所有重要信息，包括集群状态、Pod和Service信息、节点信息等。
#### kube-scheduler
kube-scheduler 是 Kubernetes 的核心组件之一，用于将新的 Pod 调度到Kubernetes 集群中的合适节点上。
#### kube-controller-manager
kube-controller-manager 是 Kubernetes 的核心组件之一，它是一个控制器，用于管理 Kubernetes 集群中的各种控制器，包括 Replication Controller、Endpoints Controller、Namespace Controller 等。
#### cloud-controller-manager
Kubernetes集群可以运行在公共云、私有云或混合云环境中。不同的云服务提供商会提供不同的API来管理他们的云资源，如虚拟机、负载均衡器、存储卷等。而cloud-controller-manager就是一种在Kubernetes集群中运行的组件，它与云服务提供商的API进行交互，从而可以让Kubernetes集群更好地与云服务提供商的资源进行集成和管理。

#### 节点组件（Node Components）
节点组件运行在每个节点上，维护运行中的 Pod 并提供 Kubernetes 运行时环境。
#### kubelet
kubelet 是 Kubernetes 的核心组件之一，它是一个代理，用于管理节点上的 Pod 和容器。
#### kube-proxy
kube-proxy 是一个网络代理，运行在集群中的每个节点上，kube-proxy 在节点上维护网络规则。 这些网络规则允许从集群内部或外部的网络会话与您的 Pod 进行网络通信。
#### 容器运行时
容器运行时是一个软件，用于在节点上运行容器。 Kubernetes 支持多种容器运行时：Docker、containerd、CRI-O、rktlet 等。

#### 插件（Add-ons）
* DNS
* Web UI (Dashboard)
* Container Resource Monitoring
* Cluster-level Logging

### Kubernetes API
Kubernetes API 是 Kubernetes 中最核心的组件之一，它提供了 Kubernetes 系统中各个组件之间的通信机制。Kubernetes API 是一个 RESTful API，通过该 API，用户可以管理 Kubernetes 集群中的各种资源，例如 Pod、Service、ReplicaSet 等等。

### 使用 Kubernetes 对象
#### 理解 Kubernetes 对象
在 Kubernetes 中，对象（Object）是 Kubernetes API 的核心概念之一。对象是 Kubernetes 集群中的可部署组件，如应用程序、服务、卷或部署等。Kubernetes 对象具有一组属性，包括元数据、规范和状态，这些属性描述了对象的特征和期望行为。

元数据（Metadata）包含了对象的名称、命名空间、标签等信息。规范（Spec）定义了对象的期望状态，包括容器的镜像、副本数量、端口等。状态（Status）则记录了对象的当前状态，比如对象是否正在运行、容器的运行状况、副本数量等信息。
#### Kubernetes 对象管理
|  管理技术  |  作用于  |  建议的环境  |
| ---- | ---- | ---- |
|  指令式命令  |  活跃对象  |  开发项目  |
|  指令式对象配置  |  单个文件  |  生产项目  |
|  声明式对象配置  |  文件目录  |  生产项目  |
---
指令式命令:使用指令式命令时，用户可以通过 kubectl 对集群中的活动对象上进行操作。因为这个技术直接在活跃对象上操作，所以它不提供以前配置的历史记录。
指令式对象配置:使用指令式对象配置时，用户可以通过 kubectl 对集群中的活动对象进行操作。与指令式命令不同的是，指令式对象配置会将对象的配置保存在文件中，这样就可以在以后对对象进行修改。
声明式对象配置:使用声明式对象配置时，用户对本地存储的对象配置文件进行操作，但是用户 未定义要对该文件执行的操作。 kubectl 会自动检测每个文件的创建、更新和删除操作。 这使得配置可以在目录上工作，根据目录中配置文件对不同的对象执行不同的操作。
#### 对象名称和ID
集群中的每一个对象都有一个名称来标识在**同类资源中**的唯一性。  
每个 Kubernetes 对象也有一个 UID 来标识在**整个集群中**的唯一性。  
比如，在同一个名字空间 中只能有一个名为 myapp-1234 的 Pod，但是可以命名一个 Pod 和一个 Deployment 同为 myapp-1234。  
对于用户提供的非唯一性的属性，Kubernetes 提供了标签（Label）和 注解（Annotation）机制。  
UID: Kubernetes 系统生成的字符串，唯一标识对象。在 Kubernetes 集群的整个生命周期中创建的每个对象都有一个不同的 UID，它旨在区分类似实体的历史事件。
#### 标签和选择器（Selector）
标签（Labels） 是附加到 Kubernetes 对象（比如 Pod）上的键值对。 标签旨在用于指定对用户有意义且相关的对象的标识属性，但不直接对核心系统有语义含义。 标签可以用于组织和选择对象。标签可以在创建时附加到对象，随后可以随时添加和修改。 每个对象都可以定义一组键/值标签。每个键对于给定对象必须是唯一的。
标签选择器: 标签选择器是一种机制，它可以根据标签来选择需要操作的对象。标签选择器有两种类型：等式选择器和集合选择器。等式选择器根据标签的键值对进行匹配，可以匹配单个键值对或多个键值对。集合选择器允许选择匹配一组标签的对象。集合选择器有三种类型：in、not in 和 exists。
#### 命名空间（Namespace）
在 Kubernetes 中，名字空间（Namespace） 提供一种机制，将同一集群中的资源划分为相互隔离的组。 同一名字空间内的资源名称要唯一，但跨名字空间时没有这个要求。

---
何时使用多个名字空间: 名字空间适用于存在很多跨多个团队或项目的用户的场景。名字空间为名称提供了一个范围。资源的名称需要在名字空间内是唯一的，但不能跨名字空间。 名字空间不能相互嵌套，每个 Kubernetes 资源只能在一个名字空间中。

---
初始命名空间  
在 Kubernetes 中，有一些默认的命名空间（Namespace）已经被定义好了，包括以下四个：
1. default：默认的命名空间，如果没有指定命名空间，则会自动选择该命名空间。
2. kube-system：这个命名空间中包含了 Kubernetes 系统的组件，例如 kube-dns、kube-scheduler、kube-controller-manager 等等。
3. kube-public：这个命名空间是为了保存集群中每个节点都可访问的数据，例如 configMap 和 secret。
4. kube-node-lease：这个命名空间是为了集群节点之间的 Lease 信息而存在的，目的是为了更好的控制节点的状态。

---
使用名字空间
```
查看名字空间
kubectl get namespace
```
```
为请求设置名字空间
kubectl run nginx --image=nginx --namespace=<名字空间名称>
kubectl get pods --namespace=<名字空间名称>
```
```
设置名字空间偏好
kubectl config set-context --current --namespace=<名字空间名称>
# 验证
kubectl config view --minify | grep namespace:<名字空间名称>
```
---
并非所有对象都在名字空间中
```
# 位于名字空间中的资源
kubectl api-resources --namespaced=true

# 不在名字空间中的资源
kubectl api-resources --namespaced=false
```
#### 注解（Annotation）
在 Kubernetes 中，注解（Annotation）是一种用于存储与对象相关的非标识性元数据的机制，可以在对象中添加任意的键值对信息，这些信息可以是可读的字符串，例如版本号、构建时间、镜像地址等等。注解并不影响 Kubernetes 对象的标识，而仅仅是提供额外的、描述性的信息，以帮助开发人员或运维人员更好地理解这个对象。

注解的值可以在对象创建时指定，也可以在运行时通过 kubectl 等命令进行修改。通过注解，可以在 Kubernetes 系统中添加关于对象的其他信息，例如对象的来源、备注、负责人、联系方式等。
#### 字段选择器
Kubernetes（K8s）字段选择器是一种查询对象的方式，可以基于对象的字段值来筛选和选择匹配的对象。它们可以用于各种 Kubernetes CLI 命令（例如 kubectl get 和 kubectl delete），也可以用于 Kubernetes API 查询中。

字段选择器支持以下操作符：
* =: 等于
* ==: 等于
* !=: 不等于
* in: 属于
* notin: 不属于
* exists: 存在
* !exists: 不存在

通过在查询中使用这些操作符和键/值对，可以对 Kubernetes 对象进行筛选和选择，
#### Finalizers
在 Kubernetes 中，Finalizers 是一个重要的概念，用于定义对象删除时的处理方式。Finalizers 是一种防止误删除 Kubernetes 对象的方法。

当一个对象被删除时，Kubernetes 控制器会检查对象的 Finalizers 列表。如果这个列表不为空，那么 Kubernetes 控制器会等待所有 Finalizers 完成后才会真正删除该对象。在这个过程中，如果一个 Finalizer 失败了，Kubernetes 控制器会将该对象标记为“DeletionTimestamp”，并重试删除操作，直到所有 Finalizers 都成功执行，然后再删除该对象。
#### 属主与附属
在 Kubernetes 中，属主与附属通常指的是资源对象之间的关系，其中一些资源对象（通常是父对象）拥有对其他资源对象（通常是子对象）的控制权。

在 Kubernetes 中，通常采用如下方式表达属主与附属关系：

通过在子对象的 metadata 中设置 ownerReferences 字段来指定属主。ownerReferences 字段是一个对象列表，每个列表元素描述了一个属主。

通过在属主的 metadata 中设置 finalizers 字段来指定附属对象的生命周期。finalizers 是一个字符串列表，每个字符串代表一个控制器。
#### 推荐使用的标签
* app.kubernetes.io/name: 应用程序名称
* app.kubernetes.io/instance: 应用程序实例名称
* app.kubernetes.io/version: 应用程序版本
* app.kubernetes.io/part-of: 应用程序的部分名称
* app.kubernetes.io/component: 应用程序组件名称
* app.kubernetes.io/managed-by: 管理该应用程序的工具的名称
* app.kubernetes.io/created-by: 由哪个资源创建
* app.kubernetes.io/environment: 应用程序所属的环境（如dev，test，prod等）
* app.kubernetes.io/revision: 应用程序的修订版本