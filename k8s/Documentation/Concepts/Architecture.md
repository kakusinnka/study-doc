## 节点
Kubernetes（K8s）是一个容器编排平台，可以管理分布式应用程序。在Kubernetes中，节点是一台物理或虚拟机器，它可以承载一个或多个Pod。节点是Kubernetes的主机，运行着Kubernetes的代理和容器运行时，它们负责维护整个Kubernetes集群。

Kubernetes节点由以下组件组成：
* kubelet: kubelet是在每个节点上运行的主机代理。它是 Kubernetes 的代理之一，负责管理节点上的容器。它还负责启动、停止和重启Pod，监控Pod的状态，以及与控制面进行通信。
* kube-proxy: kube-proxy是运行在每个节点上的网络代理，它管理Kubernetes服务的网络连接。它监视API服务器以获取服务的更改，并在节点上进行配置更改，以确保正确的路由到服务。
* 容器运行时: 节点上必须安装容器运行时，如Docker，以便能够在节点上运行容器。

节点也可以被标记和注释，以帮助组织和查找节点。标签可以用来表示节点的某些属性，注释可以用来存储与节点相关的附加信息。在Kubernetes中，节点通过节点名称来标识，可以使用kubectl命令行工具来管理和操作节点。
### 管理
向 API 服务器添加节点的方式主要有两种：
* 节点上的 kubelet 向控制面执行自注册；
* 你（或者别的什么人）手动添加一个 Node 对象。  
在你创建了 Node 对象或者节点上的 kubelet 执行了自注册操作之后，控制面会检查新的 Node 对象是否合法。
#### 节点名称唯一性
节点的名称用来标识 Node 对象。 没有两个 Node 可以同时使用相同的名称。 Kubernetes 还假定名字相同的资源是同一个对象。
#### 节点自注册
当 kubelet 标志 --register-node 为 true（默认）时，它会尝试向 API 服务注册自己。 这是首选模式，被绝大多数发行版选用。
#### 手动节点管理 
你可以使用 kubectl 来创建和修改 Node 对象。
### 节点状态
一个 k8s 节点的状态包括以下信息：
* Addresses: 节点的 IP 地址列表，可能包括多个 IP 地址。
* Conditions: 节点的运行状况，例如 Ready、OutOfDisk、MemoryPressure、DiskPressure、NetworkUnavailable 等。
* Capacity: 节点的资源容量，例如 CPU、内存、磁盘空间等。
* Allocatable: 可供使用的资源容量，即 Capacity 减去已经使用的资源。
* NodeInfo: 节点的基本信息，例如节点的名称、操作系统类型、内核版本、kubelet 版本、容器运行时版本等。
这些信息可以通过 kubectl describe node <node-name> 命令来查看。
#### 节点地址
在Kubernetes中，每个节点都有一个或多个网络标识符，以便其他Pod或节点可以访问它。这些标识符包括：
* HostName：节点的主机名，可通过kubectl describe node <node-name>或kubectl get nodes -o wide命令获取。
* ExternalIP：外部IP地址是由云提供商分配给节点的，可以用来从集群外部访问节点。
* InternalIP：内部IP地址是节点内部网络中的IP地址，可用于集群内部的通信。  
此外，还有其他地址类型，如NodeIP和PodIP。 NodeIP是节点在集群内部网络中使用的IP地址，PodIP是分配给Pod的IP地址。
#### 节点状况
节点状态（Node Status）指的是节点的运行状况，包括节点是否在线，节点的可用资源等信息。Kubernetes 通过不断地监测节点的状态来确保集群中所有的节点正常运行，并且可以调度 Pod 到可用的节点上。
#### 容量（Capacity）与可分配（Allocatable）
节点上的容量（Capacity）指的是节点所拥有的资源总量，如CPU、内存、存储等，而可分配（Allocatable）则是指节点上可供容器使用的资源总量，这些资源会被一些其他的进程（如kubelet、系统守护进程）所占用。因此，可分配的资源总量通常会比实际容量要少一些。
#### 信息（Info）
Info 指的是节点的一般信息，如内核版本、Kubernetes 版本（kubelet 和 kube-proxy 版本）、 容器运行时详细信息，以及节点使用的操作系统。 kubelet 从节点收集这些信息并将其发布到 Kubernetes API。
```
kubectl describe nodes
```
### 心跳
由 Kubernetes 节点发送的心跳可帮助您的集群确定每个节点的可用性，并在检测到故障时采取措施。

## 节点与控制面之间的通信
## 控制器
## 租约
## 云控制器管理器
## 关于 cgroup v2
## 容器运行时接口（CRI）
## 垃圾收集