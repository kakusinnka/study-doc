# k8s 配置文件
## 每个 k8s 配置文件都有的三部分
### metadata
metadata字段是配置文件的一部分，用于定义Kubernetes资源的元数据信息，包括资源的名称、命名空间、标签、注释等等。metadata字段是每个Kubernetes资源的必需字段之一，因为它们是Kubernetes控制平面管理资源的关键。控制平面根据资源的名称、命名空间、标签等元数据信息来进行资源的管理和调度。  
metadata字段中包含以下几个子字段：
1. name：资源的名称。必需的字段，必须唯一。
2. namespace：资源所属的命名空间。可选的字段，如果不指定，则默认在default命名空间中创建资源。
3. labels：资源的标签。可选的字段，用于给资源添加元数据。
4. annotations：资源的注释。可选的字段，用于添加一些描述性的信息。

### specification 规范
用于定义Kubernetes资源的规范（specification），包括资源的副本数、容器镜像、端口号、卷等等。不同的资源类型有不同的specification格式，例如Pod、Deployment、Service等等。指定了资源的规范和行为。控制平面根据资源的specification信息来进行资源的创建、更新和删除。同时，specification也是对外公开的Kubernetes API的一部分，让用户可以使用Kubernetes API来管理和操作Kubernetes资源。  
specification字段包含了以下几个子字段：
1. replicas：资源的副本数。例如，在Deployment资源中，replicas字段用于定义需要创建的Pod的数量。
2. containers：容器列表。例如，在Pod资源中，containers字段用于定义Pod中运行的容器的配置信息。
3. ports：端口列表。例如，在Service资源中，ports字段用于定义Service需要公开的端口。
4. volumes：卷列表。例如，在Pod资源中，volumes字段用于定义Pod需要使用的卷的类型和配置。

### status 状态
status字段是Kubernetes中一种特殊的字段，用于描述Kubernetes资源的状态（status）。Kubernetes的控制平面负责管理和维护每个资源的状态，当资源发生变化时，控制平面将自动更新资源的状态字段。状态字段包含了当前资源的状态信息，例如Pod资源的当前运行状态、Service资源的IP地址等等。  
status字段通常不包含在Kubernetes配置文件中，而是由Kubernetes控制平面动态地更新和维护的。但是，在某些情况下，可以使用kubectl命令来手动更新资源的状态字段。例如，可以使用kubectl命令手动更新Pod的状态字段，以标记Pod已经成功启动并且正在运行。  
需要注意的是，更新资源的状态字段通常不会影响资源的规范（specification），而只是更新资源的状态信息。这意味着更新资源的状态字段通常不会触发Kubernetes控制平面执行任何操作，而只是提供了有关资源的实时信息。

## 关于配置文件
### 配置文件格式: 可以进行线上 yaml 文件格式验证。
### 配置文件保存在哪里维护: 代码工程里 或 单独的配置库

## 组件之间的联系
Kubernetes配置文件可以使用labels和selectors字段来指定资源的标签和选择器。例如，在Deployment配置文件中，可以使用labels字段来指定Deployment的标签，然后使用selectors字段来指定哪些Pod属于这个Deployment。  
这样，当Deployment被创建时，Kubernetes将自动创建属于这个Deployment的Pod，并将它们的标签与Deployment的标签进行匹配。此后，可以使用Selectors来选择这些Pod，并对它们进行管理和访问。

### nginx-deployment.yaml
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 2
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
        image: nginx:1.16
        ports:
        - containerPort: 8080

```
### nginx-service.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080

```