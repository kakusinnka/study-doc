# 有状态的应用
## StatefulSet 基础
### 准备开始
### 教程目标
* 如何创建 StatefulSet
* StatefulSet 怎样管理它的 Pod
* 如何删除 StatefulSet
* 如何对 StatefulSet 进行扩容/缩容
* 如何更新一个 StatefulSet 的 Pod
### 创建 StatefulSet
#### 顺序创建 Pod
### StatefulSet 中的 Pod
#### 检查 Pod 的顺序索引
#### 使用稳定的网络身份标识
#### 写入稳定的存储
### 扩容/缩容 StatefulSet
#### 扩容
#### 缩容
#### 顺序终止 Pod
### 更新 StatefulSet
### 滚动更新
### OnDelete 策略
### 删除 StatefulSet
### 非级联删除
### 级联删除
### Pod 管理策略
### OrderedReady Pod 管理策略
### Parallel Pod 管理策略
### 清理现场

## 示例：使用持久卷部署 WordPress 和 MySQL
略

---
在 Kubernetes 中，PVC（PersistentVolumeClaim）是请求 Kubernetes 集群上的存储资源（PV）。PV 代表 Kubernetes 集群中的物理存储，由管理员提供和管理。PVC 允许用户声明他们的存储需求，而无需了解实际的实现。使用 PVC，应用程序可以请求存储资源，并且可以从该资源中进行扩展和缩小。可以使用 StorageClass 将存储资源（PV）提供给 PVC。

---

## 示例：使用 StatefulSet 部署 Cassandra
略
## 运行 ZooKeeper，一个分布式协调系统