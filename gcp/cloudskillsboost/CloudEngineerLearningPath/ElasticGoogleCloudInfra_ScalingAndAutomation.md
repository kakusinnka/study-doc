# 弹性 Google Cloud 基础设施：扩展和自动化
此加速点播课程向参与者介绍 Google Cloud 提供的全面且灵活的基础设施和平台服务。 通过视频讲座、演示和实践实验室的结合，参与者探索和部署解决方案元素，包括安全互连网络、负载平衡、自动扩展、基础设施自动化和托管服务。

# 课程信息
## 目标
* 将您的基础架构连接到 Google Cloud。
* 为虚拟机实例配置负载均衡器和自动缩放。
* 自动部署 Google Cloud 基础架构服务。
* 利用 Google Cloud 中的托管服务。

# 介绍
## 课程介绍
在本课程中，我们会先了解在网络之间建立互联的各种不同方案，让您可以将自己的基础架构连接到 Google Cloud。然后，我们将介绍 Google Cloud 的负载均衡和自动扩缩服务，您可以直接上手探索。接下来，我们会介绍 Terraform 等基础架构自动化服务，以便您自动部署 Google Cloud 基础架构服务。最后，让我们谈谈您可能需要使用的其他 Google Cloud 代管式服务。以下是本课程的各个单元：
1. 在网络之间建立互联
2. 负载均衡和自动扩缩
3. 基础架构自动化
4. 代管式服务

# 在网络之间建立互联
## 模块概览
在本单元中，我们将重点介绍 GCP 的混合连接产品，即 Cloud VPN、Cloud Interconnect 和 Peering。我们还将研究在 GCP 内共享 VPC 网络的选项。

## Cloud VPN
## Cloud VPN 将您的本地网络安全地连接到 Google Cloud VPC 网络
Cloud VPN 通过 IPsec VPN 隧道将您的本地网络安全地连接到 Google Cloud VPC 网络。两个网络之间传输的流量由一个 VPN 网关加密，然后由另一个 VPN 网关解密。这可以在您的数据通过公共互联网传输时对其进行保护，这就是 Cloud VPN 对于低容量数据连接非常有用的原因。

作为一项托管服务，Cloud VPN 提供 99.9% 服务可用性的 SLA，并支持站点到站点 VPN、静态和动态路由以及 IKEv1 和 IKEv2 密码。 Cloud VPN 不支持客户端计算机需要使用客户端 VPN 软件“拨入”VPN 的用例。此外，动态路由是通过 Cloud Router 配置的。

### 经典 VPN 拓扑
为了在两个 VPN 网关之间创建连接，您必须建立两个 VPN 隧道。每个隧道从其网关的角度定义连接，只有当隧道对建立后，流量才能通过。
![](../images/classic-vpn-topology.png)
> 使用 Cloud VPN 时要记住的一件事是，本地 VPN 网关的最大传输单元 (MTU) 不能大于 1460 字节。

### 高可用性 VPN
高可用性 VPN 到对等 VPN 网关拓扑
![](../images/ha-vpn-to-peer-vpn-gateway-topology.png)

高可用性 VPN 到 AWS 对等网关拓扑
![](../images/ha-vpn-to-aws-peer-gateway-topology.png)

Google Cloud 网络拓扑之间的高可用性 VPN
![](../images/ha-vpn-between-gcp-network-toplogy.png)

要使用动态路由，您需要配置云端路由器。 Cloud Router 可以使用边界网关协议 (BGP) 管理 Cloud VPN 隧道的路由。这种路由方法允许在不更改隧道配置的情况下更新和交换路由。
![](../images/dynamic-routing-with-cloud-router.png)

## 实验室介绍：配置 Google Cloud 高可用性 VPN
略

## 配置 Google Cloud 高可用性 VPN
### 概览
高可用性 VPN 是一种高可用性 (HA) Cloud VPN 解决方案，可让您在单个区域中通过 IPsec VPN 连接将您的本地网络安全地连接到 VPC 网络。高可用性 VPN 提供服务可用性达 99.99% 的服务等级协议 (SLA)。

高可用性 VPN 是一种可为各个 VPC 网络添加的区域级 VPN 解决方案。高可用性 VPN 网关有两个接口，每个接口都有自己的公共 IP 地址。创建高可用性 VPN 网关时，系统会自动从不同的地址池中选择两个公共 IP 地址。在为高可用性 VPN 配置两个隧道后，Cloud VPN 可以提供服务可用性达 99.99% 的正常运行时间。

在本实验中，您将创建一个名为 vpc-demo 的全局性 VPC，其中包含位于 us-east1 和 us-central1 两个区域的两个自定义子网。在此 VPC 中，您将在每个区域添加一个 Compute Engine 实例。然后创建名为 on-prem 的第二个 VPC 来模拟客户的本地数据中心。在第二个 VPC 中，您将在 us-central1 区域中添加一个子网和一个在该区域运行的 Compute Engine 实例。最后，您将在每个 VPC 中添加一个高可用性 VPN 和一个 Cloud Router 路由器，并从每个高可用性 VPN 网关运行两个隧道，然后再测试该配置能否达到服务等级协议 (SLA) 承诺的 99.99% 的可用性。
![](../images/HA-VPN.png)

### 目标
在本实验中，您将学习如何执行以下任务：
* 创建两个 VPC 网络和多个实例。
* 配置高可用性 VPN 网关。
* 使用 VPN 隧道配置动态路由。
* 配置全局动态路由模式。
* 验证并测试高可用性 VPN 网关的配置。

### 设置和要求
略

### 任务 1. 设置全局 VPC 环境
* 设置一个全局 VPC 和自定义子网并创建防火墙规则。
* 配置虚拟机

### 任务 2. 设置模拟的本地环境
* 设置一个全局 VPC 和自定义子网并创建防火墙规则。
* 配置虚拟机

### 任务 3. 设置高可用性 VPN 网关
* 创建高可用性 VPN 网关
* 创建 Cloud Router 路由器

### 任务 4. 创建两个 VPN 隧道
* 在 Cloud VPN 网关上创建高可用性 VPN 隧道

### 任务 5. 为每个隧道创建边界网关协议 (BGP) 对等互联
略

### 任务 6. 验证路由器配置
* 验证两个 VPC 中的路由器配置。配置防火墙规则以允许各个 VPC 之间传递流量，并验证隧道的状态。您还要验证各个 VPC 之间的 VPN 专用连接，并为 VPC 启用全局路由模式。

### 任务 7. 验证并测试高可用性 VPN 隧道的配置
略

### 任务 8. （可选）清理实验环境
略

### 任务 9. 回顾
在本实验中，您配置了高可用性 VPN 网关。您还使用 VPN 隧道配置了动态路由，并配置了全局动态路由模式。最后，您通过验证确认了高可用性 VPN 已配置且运行正常。

## 云互连和对等互连
有不同的云互连和对等服务可用于将您的基础设施连接到 Google 网络。这些服务可以分为专用连接与共享连接以及第 2 层连接与第 3 层连接。这些服务包括直接对等互连、运营商对等互连、专用互连和合作伙伴互连。

专用连接提供与 Google 网络的直接连接，但共享连接通过合作伙伴提供与 Google 网络的连接。第 2 层连接使用直接连接到 GCP 环境的 VLAN，提供与 RFC 1918 地址空间中的内部 IP 地址的连接。第 3 层连接允许使用公共 IP 地址访问 Google Workspace 服务、YouTube 和 Google Cloud API。

现在，正如我之前解释的那样，Google 还提供自己的虚拟专用网络服务，称为 Cloud VPN。该服务使用公共互联网，但流量经过加密并提供对内部 IP 地址的访问。这就是为什么 Cloud VPN 是直接对等互连和运营商对等互连的有用补充。
![](../images/Cloud-Interconnect-Peering.png)

## 专用互连
专用互连在您的本地网络和 Google 网络之间提供直接物理连接。这使您能够在网络之间传输大量数据，这比通过公共互联网购买额外的带宽更具成本效益。

为了使用专用互连，您需要在通用主机托管设施中在 Google 网络和您自己的路由器之间配置交叉连接，如下图所示。要在网络之间交换路由，您可以通过 Cloud Router 和本地路由器之间的互连配置 BGP 会话。这将允许来自本地网络的用户流量到达 VPC 网络上的 GCP 资源，反之亦然。
![](../images/Dedicated-Interconnect.png)
> 为了使用专用互连，您的网络必须在受支持的托管设施中与 Google 网络进行物理连接。“我根本不靠近这些地点之一”这时您就需要考虑合作伙伴互连。

### 合作伙伴互连
![](../images/Partner-Interconnect-02.png)
![](../images/Partner-Interconnect.png)

### 互连选项比较
![](../images/comparison-interconnect-option.png)

## 对等互联
![](../images/comparison-peering-options.png)

## 选择连接
![](../images/choosing-network-connection-option.png)
![](../images/choosing-network-connection-option-01.png)

## 共享 VPC 网络
### 共享 VPC，它允许您在 GCP 组织中的多个项目之间共享网络
共享 VPC 允许组织将多个项目的资源连接到公共 VPC 网络。这允许资源使用来自该网络的内部 IP 安全有效地相互通信。  
当您使用共享 VPC 时，您可以将一个项目指定为宿主项目，并将一个或多个其他服务项目附加到该项目。
![](../images/shared-vpc.png)

### VPC 网络对等互连，它允许您在相同或不同组织中的项目之间配置私有通信
VPC 网络对等互连允许跨两个 VPC 网络进行私有 RFC 1918 连接，无论它们是否属于同一项目或同一组织。而且每个 VPC 网络都将具有防火墙规则，用于定义网络之间允许或拒绝哪些流量。  
VPC 网络对等互连是一种去中心化或分布式的多项目网络方法，因为每个 VPC 网络可能仍处于单独管理员组的控制之下，并维护自己的全局防火墙和路由表。  
VPC 网络对等互连不会产生使用外部 IP 地址或 VPN 时存在的网络延迟、安全性和成本缺陷。
![](../images/vpc-peering.png)

### 共享 VPC 与 VPC 对等互连
如果您想在不同组织的 VPC 网络之间配置私有通信，则必须使用 VPC 网络对等互连。共享 VPC 仅在同一组织内工作。  
![](../images/shared-vpc-vs-vpc-peering.png)

两种配置之间最大的区别在于网络管理模型。共享 VPC 是多项目网络的集中式方法，因为安全和网络策略发生在单个指定的 VPC 网络中。相比之下，VPC 网络对等互连是一种去中心化方法，因为每个 VPC 网络都可以处于单独管理员组的控制之下，并维护自己的全局防火墙和路由表。
![](../images/shared-vpc-vs-vpc-peering-01.png)

## 模块回顾
在本模块中，我们研究了将基础设施连接到 GCP 的五种不同方式，它们是专用互连、合作伙伴互连、云 VPN、直接对等互连和运营商对等互连。我还为您提供了一些有关如何在不同服务之间进行选择的指导。  
我还简要概述了共享 VPC 和 VPC 网络对等互连，这是跨 GCP 项目共享 VPC 网络的两种配置。