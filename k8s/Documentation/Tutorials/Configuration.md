# 配置
## 示例：配置 java 微服务
### 使用 MicroProfile、ConfigMaps、Secrets 实现外部化应用配置
MicroProfile Config 为 Java 微服务应用程序提供了一种灵活、可扩展的配置解决方案，可以帮助开发人员更轻松地管理和更新应用程序的配置信息，从而实现更高效的应用程序开发和部署。

### 互动教程 - 配置 java 微服务
此交互式场景的目标是将两个 Java 微服务部署到 Kubernetes 并使用 MicroProfile Config、Kubernetes ConfigMaps 和 Secrets 更改它们的配置。
```
# 构建和部署 Java 微服务
# 确认 kubectl 已安装
kubectl version
# cd 到工作目录
cd sample-kubernetes-config/start/
# 构建两个 Java 微服务
mvn package -pl system
mvn package -pl inventory
# 发布
kubectl apply -f kubernetes.yaml

# 向微服务发出请求
# 查看pod状态
kubectl wait --for=condition=ready pod -l app=inventory
kubectl wait --for=condition=ready pod -l app=system
# 访问 system 服务
curl -u bob:bobpwd http://$( minikube ip ):31000/system/properties
# 访问 inventory 服务
curl http://$( minikube ip ):32000/inventory/systems/system-service

# 修改系统微服务
package system;

// CDI
import javax.enterprise.context.RequestScoped;
import javax.inject.Inject;
import javax.ws.rs.GET;
// JAX-RS
import javax.ws.rs.Path;
import javax.ws.rs.Produces;
import javax.ws.rs.core.MediaType;
import javax.ws.rs.core.Response;

import org.eclipse.microprofile.config.inject.ConfigProperty;

@RequestScoped
@Path("/properties")
public class SystemResource {

  @Inject
  @ConfigProperty(name = "APP_NAME")
  private String appName;

  @Inject
  @ConfigProperty(name = "HOSTNAME")
  private String hostname;

  @GET
  @Produces(MediaType.APPLICATION_JSON)
  public Response getProperties() {
    return Response.ok(System.getProperties())
      .header("X-Pod-Name", hostname)
      .header("X-App-Name", appName)
      .build();
  }
}

# 修改库存微服务
  // Basic Auth Credentials
  @Inject
  @ConfigProperty(name = "SYSTEM_APP_USERNAME")
  private String username;

  @Inject
  @ConfigProperty(name = "SYSTEM_APP_PASSWORD")
  private String password;

# 创建 ConfigMap 和 Secret
kubectl create configmap sys-app-name --from-literal name=my-system
kubectl create secret generic sys-app-credentials --from-literal username=bob --from-literal password=bobpwd

# 更新 Kubernetes 资源
apiVersion: apps/v1
kind: Deployment
metadata:
  name: system-deployment
  labels:
    app: system
spec:
  selector:
    matchLabels:
      app: system
  template:
    metadata:
      labels:
        app: system
    spec:
      containers:
      - name: system-container
        image: system:1.0-SNAPSHOT
        ports:
        - containerPort: 9080
        # Set the APP_NAME environment variable
        env:
        - name: APP_NAME
          valueFrom:
            configMapKeyRef:
              name: sys-app-name
              key: name
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: inventory-deployment
  labels:
    app: inventory
spec:
  selector:
    matchLabels:
      app: inventory
  template:
    metadata:
      labels:
        app: inventory
    spec:
      containers:
      - name: inventory-container
        image: inventory:1.0-SNAPSHOT
        ports:
        - containerPort: 9080
        # Set the SYSTEM_APP_USERNAME and SYSTEM_APP_PASSWORD environment variables
        env:
        - name: SYSTEM_APP_USERNAME
          valueFrom:
            secretKeyRef:
              name: sys-app-credentials
              key: username
        - name: SYSTEM_APP_PASSWORD
          valueFrom:
            secretKeyRef:
              name: sys-app-credentials
              key: password
---
apiVersion: v1
kind: Service
metadata:
  name: system-service
spec:
  type: NodePort
  selector:
    app: system
  ports:
  - protocol: TCP
    port: 9080
    targetPort: 9080
    nodePort: 31000
---
apiVersion: v1
kind: Service
metadata:
  name: inventory-service
spec:
  type: NodePort
  selector:
    app: inventory
  ports:
  - protocol: TCP
    port: 9080
    targetPort: 9080
    nodePort: 32000

# 部署您的更改
mvn package -pl system
mvn package -pl inventory
kubectl replace --force -f kubernetes.yaml
kubectl get --watch pods
curl -# -I -u bob:bobpwd -D - http://$( minikube ip ):31000/system/properties | grep -i ^X-App-Name:
```

## 使用 ConfigMap 来配置 Redis
### 教程目标
* 使用 Redis 配置的值创建一个 ConfigMap
* 创建一个 Redis Pod，挂载并使用创建的 ConfigMap
* 验证配置已经被正确应用
### 准备开始
你必须拥有一个 Kubernetes 的集群，同时你的 Kubernetes 集群必须带有 kubectl 命令行工具。
### 真实世界的案例：使用 ConfigMap 来配置 Redis
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: example-redis-config
data:
  redis-config: |
    maxmemory 2mb
    maxmemory-policy allkeys-lru    
```
```
apiVersion: v1
kind: Pod
metadata:
  name: redis
spec:
  containers:
  - name: redis
    image: redis:5.0.4
    command:
      - redis-server
      - "/redis-master/redis.conf"
    env:
    - name: MASTER
      value: "true"
    ports:
    - containerPort: 6379
    resources:
      limits:
        cpu: "0.1"
    volumeMounts:
    - mountPath: /redis-master-data
      name: data
    - mountPath: /redis-master
      name: config
  volumes:
    - name: data
      emptyDir: {}
    - name: config
      configMap:
        name: example-redis-config
        items:
        - key: redis-config
          path: redis.conf
```