# 卷
# 持久卷
## 介绍
PersistentVolume 子系统为用户和管理员提供了一组 API， 将存储如何制备的细节从其如何被使用中抽象出来。 为了实现这点，我们引入了两个新的 API 资源：PersistentVolume 和 PersistentVolumeClaim。
* 持久卷（PersistentVolume，PV） 是集群中的一块存储，可以由管理员事先制备， 或者使用存储类（Storage Class）来动态制备。 持久卷是集群资源，就像节点也是集群资源一样。PV 持久卷和普通的 Volume 一样， 也是使用卷插件来实现的，只是它们拥有独立于任何使用 PV 的 Pod 的生命周期。 此 API 对象中记述了存储的实现细节，无论其背后是 NFS、iSCSI 还是特定于云平台的存储系统。
* 持久卷申领（PersistentVolumeClaim，PVC） 表达的是用户对存储的请求。概念上与 Pod 类似。 Pod 会耗用节点资源，而 PVC 申领会耗用 PV 资源。Pod 可以请求特定数量的资源（CPU 和内存）；同样 PVC 申领也可以请求特定的大小和访问模式 （例如，可以要求 PV 卷能够以 ReadWriteOnce、ReadOnlyMany 或 ReadWriteMany 模式之一来挂载，参见访问模式）。

卷和申领的生命周期
制备
绑定
使用
保护使用中的存储对象
回收（Reclaiming）
PersistentVolume 删除保护 finalizer
预留 PersistentVolume
扩充 PVC 申领
持久卷的类型
持久卷
容量
卷模式
访问模式
类
回收策略
挂载选项
节点亲和性
阶段
PersistentVolumeClaims
访问模式
卷模式
资源
选择算符
类
使用申领作为卷
关于名字空间的说明
类型为 hostpath 的 PersistentVolume
原始块卷支持
使用原始块卷的持久卷
申请原始块卷的 PVC 申领
在容器中添加原始块设备路径的 Pod 规约
绑定块卷
对卷快照及从卷快照中恢复卷的支持
基于卷快照创建 PVC 申领
卷克隆
基于现有 PVC 创建新的 PVC 申领
卷填充器（Populator）与数据源
跨名字空间数据源
数据源引用
使用卷填充器
使用跨名字空间的卷数据源
编写可移植的配置

# 投射卷
# 临时卷
# 存储类
# 动态卷制备
# 卷快照
# 卷快照类
# CSI 卷克隆
# 存储容量
# 特定于节点的卷数限制
# 卷健康监测
# Windows 存储