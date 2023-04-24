# Pod
Pod 是可以在 Kubernetes 中创建和管理的、最小的可部署的计算单元。Pod（就像在豌豆荚中）是一组（一个或多个） 容器； 这些容器共享存储、网络、以及怎样运行这些容器的声明。Pod 类似于共享名字空间并共享文件系统卷的一组容器。
## 使用 Pod
pods/simple-pod.yaml
```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```
要创建上面显示的 Pod，请运行以下命令：
```
kubectl apply -f https://k8s.io/examples/pods/simple-pod.yaml
```
Pod 通常不是直接创建的，而是使用工作负载资源创建的。
### 用于管理 pod 的工作负载资源
通常你不需要直接创建 Pod，甚至单实例 Pod。 相反，你会使用诸如 Deployment 或 Job 这类工作负载资源来创建 Pod。 如果 Pod 需要跟踪状态，可以考虑 StatefulSet 资源。  
Kubernetes 集群中的 Pod 主要有两种用法：
* 运行单个容器的 Pod。
* 运行多个协同工作的容器的 Pod。
### Pod 怎样管理多个容器
Pod 天生地为其成员容器提供了两种共享资源：网络和存储。
![Pod](../../images/pod_01.svg)  

## 使用 Pod
### Pod 操作系统
你应该将 .spec.os.name 字段设置为 windows 或 linux 以表示你希望 Pod 运行在哪个操作系统之上。
### Pod 和控制器
你可以使用工作负载资源来创建和管理多个 Pod。 资源的控制器能够处理副本的管理、上线，并在 Pod 失效时提供自愈能力。 
### Pod 模板
工作负载资源的控制器通常使用 Pod 模板（Pod Template） 来替你创建 Pod 并管理它们。  
```
apiVersion: batch/v1
kind: Job
metadata:
  name: hello
spec:
  template:
    # 这里是 Pod 模板
    spec:
      containers:
      - name: hello
        image: busybox:1.28
        command: ['sh', '-c', 'echo "Hello, Kubernetes!" && sleep 3600']
      restartPolicy: OnFailure
    # 以上为 Pod 模板
```

## Pod 更新与替换
当某工作负载的 Pod 模板被改变时， 控制器会基于更新的模板创建新的 Pod 对象而不是对现有 Pod 执行更新或者修补操作。Kubernetes 并不禁止你直接管理 Pod。对运行中的 Pod 的某些字段执行就地更新操作还是可能的。
### 资源共享和通信
Pod 使它的成员容器间能够进行数据共享和通信。
### Pod 中的存储
一个 Pod 可以设置一组共享的存储卷。 Pod 中的所有容器都可以访问该共享卷，从而允许这些容器共享数据。 卷还允许 Pod 中的持久数据保留下来，即使其中的容器需要重新启动
### Pod 联网
在同一个 Pod 内，所有容器共享一个 IP 地址和端口空间，并且可以通过 localhost 发现对方。

## 容器的特权模式
Pod 中的所有容器都可以在特权模式下运行，以使用原本无法访问的操作系统管理权能。
### Linux 特权容器
### Windows 特权容器

## 静态 Pod
静态 Pod（Static Pod） 直接由特定节点上的 kubelet 守护进程管理， 不需要 API 服务器看到它们。

## 容器探针
Probe 是由 kubelet 对容器执行的定期诊断。

# 工作负载资源
## Deployments
一个 Deployment 为 Pod 和 ReplicaSet 提供声明式的更新能力。  
你负责描述 Deployment 中的 目标状态，而 Deployment 控制器（Controller） 以受控速率更改实际状态， 使其变为期望状态。你可以定义 Deployment 以创建新的 ReplicaSet，或删除现有 Deployment， 并通过新的 Deployment 收养其资源。

### 用例
### 创建 Deployment
下面是一个 Deployment 示例。其中创建了一个 ReplicaSet，负责启动三个 nginx Pod：
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```
1. 通过运行以下命令创建 Deployment ：
```
kubectl apply -f https://k8s.io/examples/controllers/nginx-deployment.yaml
```
2. 运行 kubectl get deployments 检查 Deployment 是否已创建。
```
kubectl get deployments

NAME                               READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/nginx-deployment   3/3     3            3           4s
```
在检查集群中的 Deployment 时，所显示的字段有：
* NAME 列出了名字空间中 Deployment 的名称。
* READY 显示应用程序的可用的“副本”数。显示的模式是“就绪个数/期望个数”。
* UP-TO-DATE 显示为了达到期望状态已经更新的副本数。
* AVAILABLE 显示应用可供用户使用的副本数。
* AGE 显示应用程序运行的时间。
3. 要查看 Deployment 上线状态，运行 kubectl rollout status deployment/nginx-deployment。
```
kubectl rollout status deployment/nginx-deployment
```
4. 要查看 Deployment 创建的 ReplicaSet（rs），运行 kubectl get rs。 输出类似于：
```
kubectl get rs

NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-85996f8dbd   3         3         3       63m
```
ReplicaSet 输出中包含以下字段：  
* NAME 列出名字空间中 ReplicaSet 的名称；
* DESIRED 显示应用的期望副本个数，即在创建 Deployment 时所定义的值。 此为期望状态；
* CURRENT 显示当前运行状态中的副本个数；
* READY 显示应用中有多少副本可以为用户提供服务；
* AGE 显示应用已经运行的时间长度。
5. 要查看每个 Pod 自动生成的标签，运行 kubectl get pods --show-labels。 输出类似于：
```
kubectl get pods --show-labels

NAME                                READY   STATUS    RESTARTS   AGE   LABELS
nginx-deployment-85996f8dbd-fhcbn   1/1     Running   0          66m   app=nginx,pod-template-hash=85996f8dbd
nginx-deployment-85996f8dbd-k5w9v   1/1     Running   0          66m   app=nginx,pod-template-hash=85996f8dbd
nginx-deployment-85996f8dbd-rdbgp   1/1     Running   0          66m   app=nginx,pod-template-hash=85996f8dbd
```
#### Pod-template-hash 标签
pod-template-hash 是 Kubernetes 中一个由 Deployment、ReplicaSet 或 StatefulSet 创建的 Pod 的标识符。每当这些控制器创建新的 Pod 时，都会为其生成唯一的 pod-template-hash 标识符，并将其添加到 Pod 的标签中。这样可以确保新 Pod 和旧 Pod 的标签不同，从而使 Kubernetes 能够轻松地将它们区分开来。
### 更新 Deployment
更新 nginx Pod 以使用 nginx:1.16.1 镜像，而不是 nginx:1.14.2 镜像。
```
kubectl set image deployment.v1.apps/nginx-deployment nginx=nginx:1.16.1
# 或者
kubectl set image deployment/nginx-deployment nginx=nginx:1.16.1
# 或者 直接编辑 nginx-deployment.yaml
将 .spec.template.spec.containers[0].image 从 nginx:1.14.2 更改至 nginx:1.16.1
```
#### 翻转（多 Deployment 动态更新）
Deployment 控制器每次注意到新的 Deployment 时，都会创建一个 ReplicaSet 以启动所需的 Pod。当 Deployment 正在上线时被更新，Deployment 会针对更新创建一个新的 ReplicaSet 并开始对其扩容，之前正在被扩容的 ReplicaSet 会被翻转: 假定你在创建一个 Deployment 以生成 nginx:1.14.2 的 5 个副本，但接下来 更新 Deployment 以创建 5 个 nginx:1.16.1 的副本，而此时只有 3 个 nginx:1.14.2 副本已创建。在这种情况下，Deployment 会立即开始杀死 3 个 nginx:1.14.2 Pod， 并开始创建 nginx:1.16.1 Pod。它不会等待 nginx:1.14.2 的 5 个副本都创建完成后才开始执行变更动作。
#### 更改标签选择算符
通常不鼓励更新标签选择算符。建议你提前规划选择算符。 在任何情况下，如果需要更新标签选择算符，请格外小心， 并确保自己了解这背后可能发生的所有事情。
### 回滚 Deployment
#### 检查 Deployment 上线历史
```
# 检查 Deployment 修订历史
kubectl rollout history deployment/nginx-deployment
# 查看修订历史的详细信息
kubectl rollout history deployment/nginx-deployment --revision=2
```
#### 回滚到之前的修订版本
```
kubectl rollout undo deployment/nginx-deployment
# 或者
kubectl rollout undo deployment/nginx-deployment --to-revision=2
```
### 缩放 Deployment
```
# 如下指令缩放 Deployment：
kubectl scale deployment/nginx-deployment --replicas=10
# 假设集群启用了Pod 的水平自动缩放， 你可以为 Deployment 设置自动缩放器，并基于现有 Pod 的 CPU 利用率选择要运行的 Pod 个数下限和上限。
kubectl autoscale deployment/nginx-deployment --min=10 --max=15 --cpu-percent=80
```
#### 比例缩放
理解：maxSurge=3，maxUnavailable=2
### 暂停、恢复 Deployment 的上线过程
```
# 使用如下指令暂停上线
kubectl rollout pause deployment/nginx-deployment

# 进行一系列 Deployment 的更新操作

# 恢复 Deployment 上线
kubectl rollout resume deployment/nginx-deployment
```
### Deployment 状态
#### 进行中的 Deployment
#### 完成的 Deployment
#### 失败的 Deployment
#### 对失败 Deployment 的操作
```
# 监视 Deployment 的进度
kubectl rollout status
# 从 kubectl rollout 命令获得的返回状态
echo $?
```
### 清理策略
你可以在 Deployment 中设置 .spec.revisionHistoryLimit 字段以指定保留此 Deployment 的多少个旧有 ReplicaSet。其余的 ReplicaSet 将在后台被垃圾回收。 默认情况下，此值为 10。
### 金丝雀部署
### 编写 Deployment 规约
#### Pod 模板
.spec 中只有 .spec.template 和 .spec.selector 是必需的字段。
#### 副本
.spec.replicas 是指定所需 Pod 的可选字段。它的默认值是1。
#### 选择算符
.spec.selector 是指定本 Deployment 的 Pod 标签选择算符的必需字段。
#### 策略
.spec.strategy 策略指定用于用新 Pod 替换旧 Pod 的策略。 .spec.strategy.type 可以是 “Recreate” 或 “RollingUpdate”。“RollingUpdate” 是默认值。
* 重新创建 Deployment: 重新创建 Deployment
* 滚动更新 Deployment: Deployment 会在 .spec.strategy.type==RollingUpdate时，采取 滚动更新的方式更新 Pod。你可以指定 maxUnavailable 和 maxSurge 来控制滚动更新 过程。
  * 最大不可用: .spec.strategy.rollingUpdate.maxUnavailable 是一个可选字段，用来指定 更新过程中不可用的 Pod 的个数上限。
  * 最大峰值: .spec.strategy.rollingUpdate.maxSurge 是一个可选字段，用来指定可以创建的超出期望 Pod 个数的 Pod 数量。
#### 进度期限秒数
.spec.progressDeadlineSeconds 是一个可选字段，用于指定系统在报告 Deployment 进展失败 之前等待 Deployment 取得进展的秒数。Deployment 控制器将在默认 600 毫秒内持续重试 Deployment。
#### 最短就绪时间
.spec.minReadySeconds 是一个可选字段，用于指定新创建的 Pod 在没有任意容器崩溃情况下的最小就绪时间， 只有超出这个时间 Pod 才被视为可用。默认值为 0（Pod 在准备就绪后立即将被视为可用）。 
#### 修订历史限制
.spec.revisionHistoryLimit 是一个可选字段，用来设定出于回滚目的所要保留的旧 ReplicaSet 数量。
#### paused（暂停的）
.spec.paused 是用于暂停和恢复 Deployment 的可选布尔字段。

## ReplicaSet
### ReplicaSet 的工作原理
ReplicaSet 的目的是维护一组在任何时候都处于运行状态的 Pod 副本的稳定集合。 因此，它通常用来保证给定数量的、完全相同的 Pod 的可用性。
### 何时使用 ReplicaSet
ReplicaSet 确保任何时间都有指定数量的 Pod 副本在运行。 然而，Deployment 是一个更高级的概念，它管理 ReplicaSet，并向 Pod 提供声明式的更新以及许多其他有用的功能。 因此，我们建议使用 Deployment 而不是直接使用 ReplicaSet， 除非你需要自定义更新业务流程或根本不需要更新。
### ReplicaSet 与 Deployment 的区别
ReplicaSet 和 Deployment 都是 Kubernetes 中的控制器，用于管理 Pod 的创建、删除和更新。它们之间的区别在于 Deployment 为 ReplicaSet 提供了高级的控制和管理功能，可以进行滚动升级、回滚、部署暂停等操作。  
具体来说，Deployment 是在 ReplicaSet 的基础上封装了一个更高级别的控制器，可以更加方便地管理 Pod 的部署和更新。Deployment 可以通过指定 Pod 的副本数和更新策略来控制 ReplicaSet 中的 Pod。Deployment 还支持滚动升级、回滚、部署暂停等操作，而这些操作在 ReplicaSet 中需要手动完成。因此，在实际使用中，一般会使用 Deployment 来管理应用的部署，而不是直接使用 ReplicaSet。
### 示例
```
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: frontend
  labels:
    app: guestbook
    tier: frontend
spec:
  # 按你的实际情况修改副本数
  replicas: 3
  selector:
    matchLabels:
      tier: frontend
  template:
    metadata:
      labels:
        tier: frontend
    spec:
      containers:
      - name: php-redis
        image: gcr.io/google_samples/gb-frontend:v3
```
```
# 创建 yaml 文件所定义的 ReplicaSet 及其管理的 Pod
kubectl apply -f https://kubernetes.io/examples/controllers/frontend.yaml
# 查看 ReplicaSet
kubectl get rs
# 查看 ReplicaSet 的状态
kubectl describe rs/frontend
# 查看启动了的 Pod 集合
kubectl get pods
# 取回运行中的某个 Pod 的 YAML：
kubectl get pods frontend-b2zdv -o yaml
```
### 非模板 Pod 的获得
尽管你完全可以直接创建裸的 Pod，强烈建议你确保这些裸的 Pod 并不包含可能与你的某个 ReplicaSet 的选择算符相匹配的标签。原因在于 ReplicaSet 并不仅限于拥有在其模板中设置的 Pod，它还可以获得其他 Pod。
### 编写 ReplicaSet 的清单
ReplicaSet 也需要 apiVersion、kind、和 metadata 字段。 对于 ReplicaSet 而言，其 kind 始终是 ReplicaSet。当控制平面为 ReplicaSet 创建新的 Pod 时，ReplicaSet 的 .metadata.name 是命名这些 Pod 的部分基础。
#### Pod 模板
.spec.template 是一个 Pod 模板， 要求设置标签。对于模板的重启策略 字段，.spec.template.spec.restartPolicy，唯一允许的取值是 Always，这也是默认值
#### Pod 选择算符
.spec.selector 字段是一个标签选择算符。
#### Replicas
你可以通过设置 .spec.replicas 来指定要同时运行的 Pod 个数。 ReplicaSet 创建、删除 Pod 以与此值匹配。  
如果你没有指定 .spec.replicas，那么默认值为 1。  
### 使用 ReplicaSet
#### 删除 ReplicaSet 和它的 Pod
当你删除 ReplicaSet 时，它会自动删除它创建的 Pod。
#### 只删除 ReplicaSet
如果你想要删除 ReplicaSet 而不删除它创建的 Pod，你可以使用 --cascade=false 选项。  
#### 将 Pod 从 ReplicaSet 中隔离
可以通过改变标签来从 ReplicaSet 中移除 Pod。
#### 扩缩 ReplicaSet
通过更新 .spec.replicas 字段，ReplicaSet 可以被轻松地进行扩缩。
#### Pod 删除开销
controller.kubernetes.io/pod-deletion-cost 是一个标签（label），用于指示在需要进行调度决策时删除 Pod 的成本。值越高，删除成本越高，Pod 越不容易被删除。
ReplicaSet 作为水平的 Pod 自动扩缩器目标
ReplicaSet 的替代方案
Deployment（推荐）
裸 Pod
Job
DaemonSet
ReplicationController
## StatefulSet
在 Kubernetes 中，StatefulSet 是一种控制器对象，用于管理运行有状态应用程序的 Pod。与 Deployment 和 ReplicaSet 不同，StatefulSet 为每个 Pod 分配唯一标识符和稳定的网络标识符（即主机名），这些标识符不会随着 Pod 在集群中的重新部署而改变。  

StatefulSet 对于运行具有状态服务的应用程序非常有用，例如数据库或消息传递系统。它们支持顺序部署，有序扩展和顺序删除 Pod，这些功能通常对于有状态应用程序很重要。当需要在有状态应用程序中进行存储时，可以使用 StatefulSet 来管理这些存储卷并确保数据的持久性。  
### 使用 StatefulSet
略
### 限制
略
### 组件
下面的示例演示了 StatefulSet 的组件。
```
# 名为 nginx 的 Headless Service 用来控制网络域名。
apiVersion: v1
kind: Service
metadata:
  name: nginx
  labels:
    app: nginx
spec:
  ports:
  - port: 80
    name: web
  clusterIP: None
  selector:
    app: nginx
---
# 名为 web 的 StatefulSet 有一个 Spec，它表明将在独立的 3 个 Pod 副本中启动 nginx 容器。
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: web
spec:
  selector:
    matchLabels:
      app: nginx # 必须匹配 .spec.template.metadata.labels
  serviceName: "nginx"
  replicas: 3 # 默认值是 1
  minReadySeconds: 10 # 默认值是 0
  template:
    metadata:
      labels:
        app: nginx # 必须匹配 .spec.selector.matchLabels
    spec:
      # 用于设置Pod在被终止前的等待时间，以便在该时间内完成正在运行的任务和清理工作。
      terminationGracePeriodSeconds: 10
      containers:
      - name: nginx
        image: registry.k8s.io/nginx-slim:0.8
        ports:
        - containerPort: 80
          name: web
        volumeMounts:
        - name: www
          mountPath: /usr/share/nginx/html
  # volumeClaimTemplates 将通过 PersistentVolume 制备程序所准备的 PersistentVolumes 来提供稳定的存储。
  volumeClaimTemplates:
  - metadata:
      name: www
    spec:
      accessModes: [ "ReadWriteOnce" ]
      storageClassName: "my-storage-class"
      resources:
        requests:
          storage: 1Gi
```
#### Pod 选择算符
略
#### 卷申领模板
略
#### 最短就绪秒数
.spec.minReadySeconds 是一个可选字段。指定控制器要等待的最小时间（以秒为单位），以确保每个新创建的Pod已准备好运行并可以接受流量。
### Pod 标识
略
#### 有序索引
略
#### 起始序号
略
#### 稳定的网络 ID
Pod DNS: web-{0..N-1}.nginx.default.svc.cluster.local  
         $(pod 名称).$(服务名称).$(名字空间).svc.cluster.local  
Pod 名称: $(StatefulSet 名称)-$(序号)
#### 稳定的存储
VolumeClaimTemplate -> PersistentVolumeClaim -> PersistentVolume  
当 Pod 或者 StatefulSet 被删除时，与 PersistentVolumeClaims 相关联的 PersistentVolume 并不会被删除。要删除它必须通过手动方式来完成。
#### Pod 名称标签
略
### 部署和扩缩保证
略
#### Pod 管理策略
略
### 更新策略
略
### 滚动更新
略
#### 分区滚动更新
略
#### 最大不可用 Pod
略
#### 强制回滚
略
### PersistentVolumeClaim 保留
略
#### 副本数
略

## DaemonSet
## Job
## 已完成 Job 的自动清理
## CronJob
## ReplicationController