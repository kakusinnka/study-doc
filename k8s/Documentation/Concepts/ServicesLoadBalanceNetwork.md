# 服务（Service）
Kubernetes 中的 Service
云原生服务发现
定义 Service
端口定义
没有选择算符的 Service
EndpointSlices
Endpoints
应用协议
多端口 Service
选择自己的 IP 地址
服务发现
环境变量
DNS
## 无头服务（Headless Services）

### 带选择算符的服务
### 无选择算符的服务
发布服务（服务类型）
NodePort 类型
LoadBalancer 类型
禁用负载均衡器节点端口分配
AWS TLS 支持
ExternalName 类型
外部 IP
粘性会话
API 对象
虚拟 IP 寻址机制

# Ingress
# Ingress 控制器
# EndpointSlice
# 网络策略
# Service 与 Pod 的 DNS
Kubernetes 为 Service 和 Pod 创建 DNS 记录。 你可以使用一致的 DNS 名称而非 IP 地址访问 Service。
* Service 的名字空间：DNS 查询可能因为执行查询的 Pod 所在的名字空间而返回不同的结果。 不指定名字空间的 DNS 查询会被限制在 Pod 所在的名字空间内。 要访问其他名字空间中的 Service，需要在 DNS 查询中指定名字空间。
* 
## Pod
### A/AAAA 记录
### Pod 的 hostname 和 subdomain 字段
### Pod 的 setHostnameAsFQDN 字段
### Pod 的 DNS 策略
### Pod 的 DNS 配置

## DNS 搜索域列表限制

## Windows 节点上的 DNS 解析

# IPv4/IPv6 双协议栈
# Topology Aware Routing
# 拓扑感知提示
# Windows 网络
# Service ClusterIP 分配
# 服务内部流量策略
# 使用拓扑键实现拓扑感知的流量路由