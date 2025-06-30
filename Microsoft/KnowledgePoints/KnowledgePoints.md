## 什么是端点管理？
端点管理（Endpoint Management） 是指对企业中所有终端设备（如电脑、手机、平板、服务器和物联网设备等）进行集中管理和控制的一种方法和技术。它的目标是确保这些设备的安全性、合规性以及高效性，同时为用户提供无缝的工作体验。

## [什么是 Windows 365？](https://learn.microsoft.com/zh-cn/windows-365/overview)
Windows 365是基于云的软件即服务 (SaaS) ，可自动为最终用户创建一种新型 Windows 虚拟机 (云电脑) 。 云电脑允许用户从各种设备（如 Windows、iOS 和 Android）访问 Windows 10 或 11。 Windows 365提供各种解决方案，以支持各种规模的组织，并提供针对特定角色和需求定制的多个部署选项。 Windows 365 可提供 Microsoft 365 的工作效率、安全性和协作优势。

Windows 365 是一种桌面即服务（DaaS）产品，但与 Azure Virtual Desktop 不同，它是一个完全托管的云 PC 服务，提供个人专属的虚拟桌面体验。

* Windows 365 Business 可简化部署，专为需要即用型云 PC 和简单管理选项的小型公司（最多 300 个席位）而设计。
* Windows 365 企业版适用于需要无限席位来创建云 PC 的大型公司。它包括根据您创建的设备映像创建自定义云 PC 的选项、更多管理选项以及与 Microsoft Intune 的完全集成。

## [什么是 Azure 虚拟桌面？](https://learn.microsoft.com/zh-cn/azure/virtual-desktop/overview)
Azure Virtual Desktop 是一种桌面即服务（DaaS）解决方案，提供托管的虚拟桌面和应用程序。它允许用户通过云访问 Windows 桌面和应用程序。

## Azure Virtual Machine
Azure Virtual Machine 是一种基础设施即服务（IaaS），允许用户在 Azure 云中创建和管理虚拟机。它是一个灵活的云计算选项，用户可以完全控制虚拟机的操作系统、软件和配置。

### 以下是 **Windows 365** 和 **Azure Virtual Desktop (AVD)** 的对比表格：
| **特性/功能**    | **Windows 365**                                          | **Azure Virtual Desktop (AVD)**                                 |
| ---------------- | -------------------------------------------------------- | --------------------------------------------------------------- |
| **概述**         | 云 PC 服务，提供全托管的虚拟桌面体验。                   | 灵活的虚拟桌面基础设施 (VDI) 解决方案。                         |
| **主要用途**     | 提供简单、固定的云 PC，适合日常办公用户。                | 提供可扩展的虚拟桌面和应用交付，适合复杂场景。                  |
| **部署与管理**   | 简化的部署和管理，面向最终用户。                         | 高度灵活，但需要 IT 专业人员进行配置和管理。                    |
| **定价模式**     | 按用户订阅，固定费用（每月/每用户）。                    | 按实际使用量计费（按小时、按资源消耗）。                        |
| **性能与资源**   | 提供预定义的虚拟机规格（如 CPU、内存、存储）。           | 用户可根据需求自定义虚拟机规格和资源分配。                      |
| **适用场景**     | - 中小企业<br>- 需要简单 IT 管理的公司<br>- 远程办公用户 | - 企业级应用<br>- 需要复杂 VDI 场景的公司<br>- 季节性或临时员工 |
| **扩展性**       | 固定配置，扩展性有限。                                   | 高度可扩展，可根据需求动态增加或减少资源。                      |
| **支持的设备**   | 支持多种设备（PC、Mac、iOS、Android 等）。               | 支持多种设备（PC、Mac、iOS、Android 等）。                      |
| **集成与兼容性** | 与 Microsoft 365 和 Azure Active Directory 深度集成。    | 与 Azure 生态系统深度集成，支持复杂的企业架构。                 |
| **网络需求**     | 需要稳定的网络连接，但优化了带宽使用。                   | 需要高质量的网络连接，尤其是对实时应用的支持。                  |
| **安全性**       | 内置 Microsoft 安全功能（如 MFA、Zero Trust）。          | 提供更灵活的安全配置，支持企业级安全策略。                      |
| **用户体验**     | 类似本地 PC 的体验，简单易用。                           | 更适合需要多用户会话或高性能的企业应用。                        |

---

### 以下是 **Azure Virtual Machine，Azure Virtual Desktop (AVD) 和 Windows 365 的对比表格：

| 特性           | Azure Virtual Machine      | Azure Virtual Desktop    | Windows 365              |
| -------------- | -------------------------- | ------------------------ | ------------------------ |
| **服务类型**   | IaaS (基础设施即服务)      | DaaS (桌面即服务)        | DaaS (桌面即服务)        |
| **用户类型**   | 开发者、IT 专业人员        | 企业用户、多用户环境     | 个人用户、企业员工       |
| **控制级别**   | 完全控制（OS、应用、硬件） | 部分控制（桌面和应用）   | 最少控制（完全托管）     |
| **灵活性**     | 高                         | 中                       | 低                       |
| **多用户支持** | 不支持                     | 支持（多会话）           | 不支持（每用户独占资源） |
| **管理复杂性** | 高                         | 中                       | 低                       |
| **定价模式**   | 按使用量付费               | 按需扩展                 | 按用户订阅               |
| **典型用途**   | 应用托管、开发测试         | 远程办公、多用户虚拟桌面 | 专属云 PC，简单部署      |

---

## Windows 即服务（Windows as a Service，WaaS）
是微软推出的一种全新操作系统更新和管理模式，主要针对 Windows 10 和 Windows 11。WaaS 的核心理念是通过持续的功能更新和安全更新，提供一种更灵活、更高效的操作系统交付方式，避免传统的“大版本发布”模式。

### Windows 客户端有两种发布类型：
* 功能更新增加了新功能，每年发布两次。由于这些更新的频率较高，因此它们的规模较小。
* 质量更新提供安全性和可靠性修复。这些更新以非安全版本或安全+非安全组合版本的形式每月发布一次。非安全版本允许 IT 管理员对内容进行早期验证。此外，还会发布累积更新，其中包括之前的所有更新。

### 有三种服务通道。每个通道在何时将这些更新发送到客户端计算机方面都具有不同程度的灵活性。
* Windows Insider 计划为企业提供了测试和反馈将在下一个功能更新中发布的功能的机会。新功能将在开发周期内通过一个称为 "飞行 "的过程交付给 Windows Insider 社区。该流程将使企业能够准确了解微软正在开发的功能，并尽快开始测试。微软建议所有组织至少有几台设备注册该计划。
* 一般可用性通道每年都会收到功能更新发布的新功能。这种模式非常适合试点部署和功能更新测试。对于需要使用最新功能的开发人员等用户来说，它也是理想之选。一旦最新版本通过试点部署和测试，企业就可以选择何时部署更新。
* 长期服务渠道专为不运行 Office 应用程序的专业系统和设备（如医疗设备或 ATM）而设计。这些设备通常只执行单一任务，与组织中的其他设备相比不需要频繁更新。这种渠道每两三年就会获得新功能。

## OOBE（Out of Box Experience，开箱即用体验）
是指用户首次使用新设备或软件时的初始设置流程和用户体验，主要用于帮助用户快速完成设备或系统的基本配置，使其能够立即投入使用。在 Windows 系统中，OOBE 是用户在首次启动设备时看到的设置向导，涵盖语言选择、网络连接、账户登录等一系列步骤。

## Windows Autopilot
是微软推出的一种现代化设备部署和管理解决方案，旨在简化 Windows 设备的初始设置、配置和管理过程。通过 Windows Autopilot，企业可以实现零接触部署（Zero-touch Deployment），让新设备直接交付给最终用户，无需 IT 部门手动配置。

## Just-In-Time (JIT)
Just-In-Time (JIT) 访问是一种安全模型，只有在特定任务或时间段内，才会授予用户或系统对敏感资源的访问权限。任务完成或时间到期后，权限会自动撤销。

## Just-Enough-Access (JEA)
Just-Enough-Access (JEA) 是一种基于最小权限原则的安全管理方法，确保用户或系统只拥有完成特定任务所需的最低权限，而不会授予不必要的访问权限。

## 什么是 Enclave（安全区）？エンクレーブ
Enclave 是一种基于硬件的安全隔离技术，用于保护敏感数据和代码，即使在操作系统被入侵或存在恶意软件的情况下，也能确保数据和代码的安全。它通过创建一个受保护的内存区域，防止未经授权的访问和修改，从而实现高度的安全性。

这种技术通常应用于需要保护非持久化数据（如 RAM 或 CPU 缓存中的数据）的场景，特别是在云计算、数据隐私保护和高安全性应用中。

## 什么是 PHS（密码哈希同步，Password Hash Synchronization）？パスワード ハッシュの同期
密码哈希同步（PHS） 是一种用于在混合身份环境中实现身份验证的机制，主要用于将本地 Active Directory（AD）中的用户密码哈希同步到 Microsoft Entra ID（以前称为 Azure AD）。它是 Microsoft 提供的一种简单、高效的混合身份解决方案。

在 PHS 模式下，用户可以使用相同的用户名和密码访问本地资源和云资源（如 Microsoft 365）。PHS 通过将密码哈希存储在 Microsoft Entra ID 中，允许 Microsoft Entra ID 直接处理用户的身份验证请求，而无需依赖本地 Active Directory。

## 什么是 PTA（Pass-through Authentication，直通认证）？パススルー
Pass-through Authentication（PTA） 是一种用于在混合身份环境中实现用户身份验证的机制。PTA 允许用户使用其本地 Active Directory（AD）凭据直接登录到云服务（如 Microsoft 365），而无需将密码哈希同步到 Microsoft Entra ID（以前称为 Azure AD）。这种方法通过一个安全的代理将密码验证请求从云端传递到本地 AD。

PTA 提供了一种简单而安全的方式来实现单一登录（SSO），同时确保用户凭据不离开企业的本地环境。

## 以下是 **PHS（Password Hash Synchronization, 密码哈希同步）** 和 **PTA（Pass-through Authentication, 直通认证）** 的详细对比表：

| **对比维度**            | **PHS（密码哈希同步）**                                                                                     | **PTA（直通认证）**                                                                                                        |
| ----------------------- | ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **工作原理**            | 将本地 Active Directory 中的用户密码哈希同步到 Microsoft Entra ID，用户登录时由 Microsoft Entra ID 验证。   | 用户登录时，Microsoft Entra ID 将密码验证请求通过 PTA 代理转发到本地 Active Directory 进行验证。                           |
| **密码存储位置**        | 用户密码的哈希值存储在 Microsoft Entra ID（经过二次加密处理）。                                             | 用户密码始终存储在本地 Active Directory，密码验证也在本地完成。                                                            |
| **密码安全性**          | 密码哈希经过二次加密后存储在云端，安全性较高，但仍有云端存储的风险。                                        | 密码从不离开本地环境，安全性更高，降低了密码泄露的可能性。                                                                 |
| **密码更改生效时间**    | 用户密码在本地更改后，需要等待同步到 Microsoft Entra ID，可能有一定时间延迟。                               | 用户密码在本地更改后立即生效，无需等待同步。                                                                               |
| **对本地 AD 的依赖**    | 用户登录云端资源时，不依赖本地 Active Directory 的可用性。                                                  | 用户登录云端资源时，依赖本地 Active Directory 和 PTA 代理的可用性。                                                        |
| **高可用性**            | 即使本地 Active Directory 不可用，用户仍然可以通过 Microsoft Entra ID 登录云资源。                          | 如果本地 Active Directory 或 PTA 代理不可用，用户将无法登录云资源。                                                        |
| **支持智能卡/证书认证** | 不支持智能卡或证书认证。                                                                                    | 不支持智能卡或证书认证。                                                                                                   |
| **部署复杂性**          | 部署简单，只需配置 Azure AD Connect 并启用密码哈希同步功能。                                                | 部署稍复杂，需要安装和配置一个或多个 PTA 代理，并确保其与 Microsoft Entra ID 和本地 AD 的通信畅通。                        |
| **多重身份验证（MFA）** | 支持与 Microsoft Entra ID 的多重身份验证（MFA）集成。                                                       | 支持与 Microsoft Entra ID 的多重身份验证（MFA）集成。                                                                      |
| **适用场景**            | - 企业希望简化混合身份管理，且对密码存储在云端没有顾虑。<br> - 企业需要高可用性，不依赖本地 AD 登录云资源。 | - 企业希望用户密码不离开本地环境，增强安全性。<br> - 企业需要用户密码更改后立即生效。<br> - 企业需要严格控制身份验证过程。 |
| **成本**                | 无需额外的硬件或代理，成本较低。                                                                            | 需要部署 PTA 代理，但无需额外硬件，成本适中。                                                                              |

---

## 以下是关于 **Microsoft Teams 功能** 的知识点总结表格：

| **功能名称**        | **最大参与人数**                             | **主要用途**                       | **支持的工具**                       | **角色分配**           | **适用场景**                                   |
| ------------------- | -------------------------------------------- | ---------------------------------- | ------------------------------------ | ---------------------- | ---------------------------------------------- |
| **ライブ イベント** | 最大 20,000 人                               | 大规模直播活动，单向信息传递       | Microsoft Stream、Teams、Viva Engage | 制作人、发言人、组织者 | 公司级别的大型直播活动，如全员大会、产品发布会 |
| **ウェビナー**      | 最大 1,000 人（前 1,000 人享有完整互动功能） | 小规模、高互动的在线会议或培训     | Microsoft Teams                      | 无明确角色分配         | 客户培训、团队会议、互动性较强的在线活动       |
| **チャネル**        | 无限制                                       | 团队内部的项目或话题讨论           | Microsoft Teams                      | 无                     | 团队协作、项目管理、话题讨论                   |
| **電話会議**        | 最大 1,000 人                                | 语音会议，适用于网络连接受限的情况 | 电话拨入                             | 无                     | 语音会议、电话拨入式会议                       |

---

## [介绍 Microsoft 365 中的工作管理工具](https://learn.microsoft.com/en-us/training/modules/describe-productivity-solutions-microsoft-365/4-describe-work-management-tools)

## [在线会议](https://learn.microsoft.com/en-us/training/modules/describe-collaboration-solutions-microsoft-365/3-workloads-teams-value-they-provide)
* 音频会议最多允许 1000 名电话与会者参加。

### 团队会议 Meetings 
团队会议包括音频、视频和屏幕共享，最多可容纳 1,000 人。仅限观看的功能适用于 1,000 人以上至 20,000 人的参与者。与会者无需是组织成员（或拥有团队账户）即可加入团队会议。他们可以通过日历邀请中的 "加入会议 "链接直接加入，也可以通过音频方式加入（如果有的话）。

### 网络研讨会 Webinars 
网络研讨会是一种结构化会议，主讲人和参与者都有明确的角色定位，通常用于培训目的或销售和营销线索生成场景。网络研讨会提供双向互动。最多可有 1,000 人参加，具有完全互动功能。

### 实时活动 Live events 
实时活动是一种结构化会议，使您的组织能够安排和制作流媒体活动，并将其传送给多达 20,000 名参与者的大量在线受众。即时活动提供可管理的问答体验。无论受众、团队或社区在哪里，您都可以使用 Teams 或 Microsoft Stream、Teams 创建实时活动。

## Microsoft 365 应用程序的三种主要更新渠道：
* 当前频道（Current Channel 最新チャネル）会在功能更新完成后立即接收更新，但没有固定的时间表。该频道每月还会接收两到三次安全和非安全更新。微软推荐使用此渠道，因为它能在 Office 最新功能准备就绪时立即为用户提供这些功能。
* 每月企业频道（Monthly Enterprise Channel 月次エンタープライズ チャネル）每月第二个星期二接收一次功能更新。该月度更新可包括功能、安全和非安全更新。如果您希望按照可预测的发布计划每月为用户提供一次 Office 新功能，Microsoft 建议您使用此渠道。
* 半年度企业频道（Semi-Annual Enterprise Channel 半期エンタープライズ チャネル）每六个月（1 月和 7 月的第二个星期二）接收一次功能更新。此更新可包括功能、安全和非安全更新。Microsoft 建议该渠道仅用于企业中需要在推出 Office 新功能前进行大量测试的特定设备。

## [Teams 频道功能比较](https://learn.microsoft.com/en-us/microsoftteams/teams-channels-overview#channel-feature-comparison)

## 什么是密码哈希与 Microsoft Entra ID 同步？ パスワード ハッシュ同期
密码散列同步是用于实现混合身份的登录方法之一。Microsoft Entra Connect 将用户密码的哈希值从内部活动目录实例同步到基于云的 Microsoft Entra 实例。

## 什么是 Microsoft Entra 直通式身份验证？ パススルー認証
Microsoft Entra 直通式身份验证允许用户使用相同的密码登录内部部署和基于云的应用程序。

## 什么是 Microsoft Entra ID 联合？ フェデレーション認証
联盟是已建立信任的域的集合。信任的程度可能不同，但通常包括身份验证，几乎总是包括授权。一个典型的联盟可能包括几个组织，这些组织已经建立了信任，可以共享一组资源。

## 用户订购许可证 user subscription licenses (USLs)
Microsoft 365 产品和服务以用户订购许可证 (USL) 的形式提供，并按每个用户授予许可。访问 Microsoft 365 产品和服务的每个用户都需要分配一个 USL。管理员在 Microsoft 365 管理中心管理许可证。他们可以将许可证分配给单个用户或访客帐户。以下列表介绍了可用选项：
* Full USLs：全额 USL 适用于以前未购买过 Microsoft 产品和服务的新客户。适用于首次购买 Microsoft 365 的用户。提供完整的 Microsoft 365 产品和服务访问权限。
* Add-on USLs：附加 USL 适用于希望添加 Microsoft 365 云产品和服务的内部部署软件客户。为现有 Microsoft 产品用户提供额外功能或服务。
* From SA USLs：SA USL 适用于希望过渡到云的内部部署软件保障客户。适用于从传统软件保障（Software Assurance, SA）模式转向订阅模式的用户。用户可以通过 From SA USL 将现有的永久许可证转为订阅许可证。
* Step Up USLs：升级 USL 适用于希望提升服务级别的客户。允许用户从较低级别的订阅（如 Microsoft 365 E3）升级到更高级别的订阅（如 Microsoft 365 E5）。提供灵活的升级路径。

## [Microsoft 账单帐户类型](https://learn.microsoft.com/en-us/microsoft-365/commerce/manage-billing-accounts?view=o365-worldwide#what-are-the-types-of-billing-accounts)
当您注册试用或购买 Microsoft 产品时会创建一个账单帐户。您可以使用账单帐户管理帐户设置、发票、付款方式和购买。Microsoft 365 管理中心目前支持以下类型的账单帐户：
* Microsoft Customer Agreement (MCA): Microsoft 客户协议 (MCA)：当您的组织与 Microsoft 代表、授权合作伙伴合作或独立购买产品和服务时，就会创建此计费帐户。
* Microsoft Partner Agreement (MPA): 微软合作伙伴协议 (MPA)：此计费帐户是为云解决方案提供商 (CSP) 合作伙伴创建的，用于管理他们的客户。
* Microsoft Online Subscription Agreement (MOSA): Microsoft 在线订购协议 (MOSA)：此计费帐户是在您直接注册 Microsoft 365 订阅时创建的。如果您的帐户尚未转入 Microsoft 客户协议，则可能拥有 MOSA 帐户。对于 MOSA 帐户，您会在帐户周年日收到每笔订单的发票。

## [Microsoft 365 服务的支持选项](https://learn.microsoft.com/en-us/training/modules/describe-support-offerings-for-microsoft-365-services/2-explore-support-options)

### 支持类型与描述

| 支持类型                         | 描述                                                                                                                                                                                     |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **社区支持**                     | 您的组织可以通过 [Microsoft 365 社区](https://answers.microsoft.com/) 或 [Microsoft 支持社区](https://community.microsoft.com/) 获取社区支持，与他人协作、提问并解决问题。               |
| **自助支持**                     | 您的组织可以通过 Microsoft 365 管理中心的“帮助与支持”按钮或导航至 [联系 Microsoft 支持](https://support.microsoft.com/) 获取帮助。若推荐的指导或文章未能解决问题，可联系技术支持。       |
| **网络聊天、电子邮件和电话支持** | 您的组织可以通过电子邮件、在线聊天或电话提交技术、账单和订阅支持问题。详情请参阅 [联系我们 - Microsoft 支持](https://support.microsoft.com/contactus)。                                  |
| **问答论坛和在线帮助**           | 通过 [Microsoft Q&A](https://learn.microsoft.com/answers/) 或 [Microsoft Learn](https://learn.microsoft.com/) 获取有关 Microsoft 技术的准确答案和在线帮助。                              |
| **售前支持**                     | 提供订阅功能、优势以及 Microsoft 365 服务购买决策方面的帮助。                                                                                                                            |
| **FastTrack 服务**               | FastTrack 是 Microsoft 提供的服务，帮助客户快速上手 Microsoft 云解决方案并推动用户采用。适用于 Microsoft 365、Azure 或 Dynamics 365 的合格订阅客户。此服务在订阅期间免费提供。           |
| **Microsoft Unified 支持**       | 提供全面支持服务，包括全天候技术支持、指定的客户成功经理、顾问支持、云协助、技术培训等。                                                                                                 |
| **通过 Microsoft 合作伙伴支持**  | 如果您的组织通过云服务提供商 (CSP) 购买了 Microsoft 365 订阅，则可以直接通过认证的 Microsoft 365 合作伙伴获得支持。CSP 将作为第一线支持，并在无法解决问题时升级至 Microsoft。            |
| **其他支持选项**                 | 您的组织可以安装 Microsoft 支持和恢复助手，通过运行测试来识别问题并提供最佳解决方案。目前可修复 Office、Microsoft 365 或 Outlook 问题。小型企业可以使用 Business Assist 获得全天候支持。 |

--- 

## [微软的端点管理](https://learn.microsoft.com/en-us/intune/endpoint-manager-overview)

## [什么是高级认证？先進認証](https://learn.microsoft.com/ja-jp/microsoft-365/enterprise/hybrid-modern-auth-overview?view=o365-worldwide#BKMK_WhatisModAuth)

