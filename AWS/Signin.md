# [什么是 AWS Sign-In？](https://docs.aws.amazon.com/zh_cn/signin/latest/userguide/what-is-sign-in.html)
本指南可帮助您了解登录 Amazon Web Services (AWS) 的不同方式，具体取决于您的用户类型。

## 确定您的用户类型
登录方式取决于您的 AWS 用户类型。  
您可以作为根用户、IAM 用户、IAM 身份中心中的用户或联合身份管理 AWS 账户。  
您可以使用 AWS Builder ID 配置文件访问某些 AWS 服务和工具。  

### 根用户
也称为账户所有者或账户根用户。  
作为根用户，您可以完全访问您的 AWS 账户中的所有 AWS 服务和资源。  
首次创建 AWS 账户时，您将从一个可以完全访问账户中所有 AWS 服务和资源的单点登录身份开始。  
此身份是 AWS 账户根用户。  
您可以使用创建账户时使用的电子邮件地址和密码以根用户身份登录。  
根用户使用 AWS 管理控制台登录。  
有关如何登录的分步说明，请参阅[以根用户身份登录 AWS 管理控制台](#以-root-用户身份登录)。

### IAM 用户
IAM 用户是您在 AWS 中创建的实体。此用户是您 AWS 账户内被授予特定自定义权限的身份。  
您的 IAM 用户凭证由用于登录 AWS 管理控制台的名称和密码组成。有关如何登录的分步说明，请参阅以 IAM 用户身份登录 AWS 管理控制台。

### IAM 身份中心用户
IAM 身份中心用户是 AWS 组织的成员，可以通过 AWS 访问门户获得对多个 AWS 账户和应用程序的访问权限。  
如果他们的公司已将 Active Directory 或其他身份提供商与 IAM 身份中心集成，则 IAM 身份中心中的用户可以使用其公司凭证登录。  
IAM 身份中心也可以是身份提供商，管理员可以在其中创建用户。  
无论身份提供商是谁，IAM 身份中心中的用户都使用 AWS 访问门户登录，这是其组织的特定登录 URL。  
IAM 身份中心用户无法通过 AWS 管理控制台 URL 登录。

### 联合身份
联合身份是可以使用知名的外部身份提供商 (IdP) 登录的用户，例如使用 Amazon、Facebook、Google 或任何其他与 OpenID Connect (OIDC) 兼容的 IdP 登录。  
借助 Web 身份联合，您可以接收身份验证令牌，然后将该令牌交换为 AWS 中的临时安全凭证，这些凭证映射到具有使用 AWS 账户中资源权限的 IAM 角色。  
您无需使用 AWS 管理控制台或 AWS 访问门户登录。相反，所使用的外部身份决定了您的登录方式。

### AWS Builder ID 用户


## 确定您的登录网址
根据您属于哪种 AWS 用户，使用以下 URL 之一访问 AWS。

### AWS 账户根用户登录 URL
根用户从 [AWS 登录页面](https://console.aws.amazon.com/) 访问 AWS 管理控制台。此登录页面还提供以 IAM 用户身份登录的选项。

### AWS 访问门户
AWS 访问门户是 IAM Identity Center 中用户登录和访问您的帐户的特定登录 URL。  
当管理员在 IAM Identity Center 中创建用户时，管理员可以选择用户是收到加入 IAM Identity Center 的电子邮件邀请，或是收到来自管理员或服务台员工的包含一次性密码和 AWS 访问门户 URL 的消息。

### IAM 用户登录 URL
IAM 用户可以使用特定的 IAM 用户登录 URL 访问 AWS 管理控制台。IAM 用户登录 URL 结合了您的 AWS 账户 ID 或别名以及 signin.aws.amazon.com/console

### 联合身份 URL
联合身份的登录 URL 各不相同。外部身份或外部身份提供商 (IdP) 决定联合身份的登录 URL。外部身份可以是 Windows Active Directory、使用 Amazon 登录、Facebook 或 Google。

### AWS Builder ID URL
您的 AWS Builder ID 配置文件的 URL 为 **https://profile.aws.amazon.com/** 。使用您的 AWS Builder ID 时，登录 URL 取决于您要访问的服务。例如，要登录 Amazon CodeCatalyst，请转到 **https://codecatalyst.aws/login** 。

## AWS 账户管理员的安全最佳实践
如果您是创建了新 AWS 账户的账户管理员，我们建议您执行以下步骤以帮助您的用户在登录时遵循 AWS 安全最佳实践。

1. 以根用户身份登录以启用多重身份验证 (MFA)，并在 IAM Identity Center 中创建 AWS 管理用户（如果您尚未这样做）。然后，保护您的根凭证，不要将它们用于日常任务。
2. 以 AWS 账户管理员身份登录并设置以下身份：
   1. 为其他人创建最低权限用户。
   2. 为工作负载设置临时凭证。
   3. 仅为需要长期凭证的用例创建访问密钥。
3. 添加权限以授予这些身份的访问权限。您可以开始使用 AWS 托管策略，并转向最低权限。
   1. 向 AWS IAM Identity Center（AW​​S Single Sign-On 的后继者）用户添加权限集。
   2. 向用于工作负载的 IAM 角色添加基于身份的策略。
   3. 为需要长期凭证的用例为 IAM 用户添加基于身份的策略。
4. 保存并共享有关登录 AWS 管理控制台的信息。此信息会有所不同，具体取决于您创建的身份类型。
5. 保持您的根用户电子邮件地址和主要帐户联系电话号码为最新，以确保您可以收到重要的帐户和安全相关通知。
   1. 修改 AWS 帐户根用户的帐户名称电子邮件地址或密码。
   2. 访问或更新主要帐户联系人。
6. 查看 [IAM 中的安全最佳实践](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) ，了解更多身份和访问管理最佳实践。

# 登录 AWS 管理控制台
## 以根用户身份登录 AWS 管理控制台
首次创建 AWS 账户时，您将从一个登录身份开始，该身份具有对账户中所有 AWS 服务和资源的完全访问权限。  
此身份称为 AWS 账户根用户，可使用您创建账户时使用的电子邮件地址和密码登录来访问。

### 以 root 用户身份登录
1. 打开 AWS [管理控制台](https://console.aws.amazon.com/) 。
2. 选择根用户。
3. 在根用户电子邮件地址下，输入与您的根用户关联的电子邮件地址。然后，选择下一步。
4. 如果系统提示您完成安全检查，请输入显示的字符以继续。如果您无法完成安全检查，请尝试收听音频或刷新安全检查以获取一组新字符。
5. 输入您的密码。
6. 使用 MFA 进行身份验证。
7. 选择登录。系统将显示 AWS 管理控制台。

## 以 IAM 用户身份登录 AWS 管理控制台
IAM 用户是在 AWS 账户内创建的身份，具有与 AWS 资源交互的权限。  
IAM 用户使用其账户 ID 或别名、用户名和密码登录。 IAM 用户名由您的管理员配置。  

### 要以 IAM 用户身份登录
1. 打开 AWS [管理控制台](https://console.aws.amazon.com/) 。
2. 出现主登录页面。输入账户 ID（12 位数字）或别名、您的 IAM 用户名和密码。
3. 选择登录。
4. 如果为 IAM 用户启用了 MFA，AWS 会要求您使用身份验证器确认您的身份。有关更多信息，请参阅在 AWS 中使用多重身份验证 (MFA)。

# 登录 AWS 访问门户
IAM 身份中心中的用户是 AWS 组织的成员。  
IAM 身份中心中的用户可以通过使用特定登录 URL 登录 AWS 访问门户来访问多个 AWS 账户和业务应用程序。

## 登录 AWS 访问门户
1. 在浏览器窗口中，粘贴通过电子邮件提供的登录 URL，例如 https://your_subdomain.awsapps.com/start。然后按 Enter。
2. 使用您的公司凭证（如用户名和密码）登录。
3. 如果系统要求您输入验证码，请检查您的电子邮件。然后将验证码复制并粘贴到登录页面。
4. 如果在 IAM 身份中心为您的用户启用了 MFA，则您可以使用它进行身份验证。
5. 经过身份验证后，您可以访问门户中显示的任何 AWS 账户和应用程序。
   1. 要登录 AWS 管理控制台，请选择“账户”选项卡，然后选择要管理的个人账户。此时将显示您用户的角色。 选择账户的角色名称以打开 AWS 管理控制台。 选择“访问密钥”以获取命令行或编程访问的凭据。
   2. 选择“应用程序”选项卡以显示可用的应用程序，然后选择要访问的应用程序的图标。

> 以用户身份登录 IAM 身份中心后，您将获得在一定时间段内访问资源的凭证，这称为会话。  
> 默认情况下，用户可以登录 AWS 账户 8 小时。  
> IAM 身份中心管理员可以指定不同的持续时间，从最短 15 分钟到最长 90 天。  
> 会话结束后，您可以再次登录。

# 通过 AWS 命令​​行界面登录
如果您计划使用 AWS 命令​​行界面，我们建议您在 IAM Identity Center 中配置用户。  
AWS 访问门户用户界面使 IAM Identity Center 用户可以轻松选择 AWS 账户并使用 AWS CLI 获取临时安全凭证。  
您还可以直接配置 AWS CLI 以使用 IAM Identity Center 对用户进行身份验证。

要使用 IAM Identity Center 凭证通过 AWS CLI 登录
1. 请检查您是否已完成 [先决条件](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sso.html#sso-configure-profile-prereqs)。
2. 如果您是首次登录，请使用 [aws configure sso 向导](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sso.html#sso-configure-profile-token-auto-sso) 配置您的配置文件。
3. 配置配置文件后，运行以下命令，然后按照终端中的提示进行操作。
```
aws sso login --profile my-profile
```

# 以联合身份登录
联合身份是可以使用外部身份访问安全 AWS 账户资源的用户。  
外部身份可以来自企业身份存储（例如 LDAP 或 Windows Active Directory）或第三方（例如使用 Amazon、Facebook 或 Google 登录）。  
联合身份不使用 AWS 管理控制台或 AWS 访问门户登录。  
使用的外部身份类型决定了联合身份如何登录。

# 使用 AWS Builder ID 登录
AWS Builder ID 是一种个人资料，可供访问精选工具和服务，包括 Amazon CodeCatalyst、Amazon Q Developer 以及 AWS 培训和认证。  
AWS Builder ID 代表您个人，独立于您现有 AWS 账户中可能拥有的任何凭证和数据。与其他个人资料一样，AWS Builder ID 会随着您实现个人、教育和职业目标而不断陪伴您。

您的 AWS Builder ID 可以补充您可能已经拥有或想要创建的任何 AWS 账户。  
虽然 AWS 账户充当您创建的 AWS 资源的容器并为这些资源提供安全边界，但您的 AWS Builder ID 代表您个人。

## 创建您的 AWS Builder ID
您可以在注册使用 AWS Builder ID 的 AWS 工具和服务时创建它。在注册 AWS 工具或服务的过程中，请使用您的电子邮件地址、姓名和密码进行注册。

使用 AWS Builder ID 的工具和服务会在需要时指导您创建和使用您的 AWS Builder ID。

## 使用 AWS Builder ID 的 AWS 工具和服务
### AWS 云社区
Community.aws 是一个由 AWS 构建者社区创建的平台，您可以使用 AWS 构建者 ID 访问该平台。  
在这里，您可以发现教育内容、分享个人想法和项目、评论他人的帖子以及关注您最喜欢的构建者。

### Amazon CodeCatalyst
当您开始使用 Amazon CodeCatalyst 时，您将创建一个 AWS 构建者 ID，并选择一个与问题、代码提交和拉取请求等活动相关联的别名。  
邀请其他人加入您的 Amazon CodeCatalyst 空间，该空间配备了您的团队构建下一个成功项目所需的工具、基础设施和环境。  
您需要一个 AWS 账户才能将新项目部署到云中。

### AWS 迁移中心
使用您的 AWS 构建者 ID 访问 AWS 迁移中心 (Migration Hub)。  
迁移中心提供了一个单一的位置来发现您现有的服务器、规划迁移并跟踪每个应用程序迁移的状态。

### Amazon Q Developer
Amazon Q Developer 是一款基于 AI 的生成式对话助手，可帮助您理解、构建、扩展和操作 AWS 应用程序。

### AWS re:Post
AWS re:Post 为您提供专家技术指导，以便您使用 AWS 服务更快地进行创新并提高运营效率。  
您可以使用您的 AWS Builder ID 登录并加入 re:Post 社区，无需 AWS 账户或信用卡。

### AWS 初创公司
使用您的 AWS Builder ID 加入 AWS 初创公司，在那里您可以使用学习内容、工具、资源和支持通过 AWS 发展您的初创公司。

### AWS 培训和认证
您可以使用您的 AWS Builder ID 访问 AWS 培训和认证，在那里您可以使用 AWS Skill Builder 构建您的 AWS 云技能，向 AWS 专家学习，并使用行业认可的凭证验证您的云专业知识。

### 网站注册门户 (WRP)
您可以将您的 AWS Builder ID 用作 AWS 营销网站的持久客户身份和注册配置文件。  
要注册新的网络研讨会并查看您已注册或参加过的所有网络研讨会，请参阅我的网络研讨会。

## 编辑您的 AWS Builder ID 配置文件
略

## 更改您的 AWS Builder ID 密码
略

## 删除您的 AWS Builder ID 的所有活动会话
在已登录的设备下，您可以查看您当前登录的所有设备。  
如果您不认识某个设备，作为安全最佳实践，请先更改密码，然后从所有设备退出。  
您可以通过在 AWS Builder ID 的安全页面上删除所有活动会话来从所有设备退出。

## 删除您的 AWS Builder ID
略

## 管理 AWS Builder ID 多重身份验证 (MFA)
略

## AWS Builder ID 中的隐私和数据
略

## AWS Builder ID 和其他 AWS 凭证
您的 AWS Builder ID 与任何 AWS 账户或登录凭证都是分开的。您可以将同一个电子邮件用作您的 AWS Builder ID 和 AWS 账户的根用户电子邮件。

# 退出 AWS
略

# 解决 AWS 账户登录问题
略

# 排查 AWS Builder ID 问题
略