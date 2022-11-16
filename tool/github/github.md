# authentication
## connecting-to-github-with-ssh
您可以使用安全外壳协议 (Secure Shell Protocol) (SSH) 连接到 GitHub，该协议为不安全的网络提供安全通道。
### About SSH
使用 SSH 协议，您可以连接到远程服务器和服务并对其进行身份验证。使用 SSH 密钥，您可以连接到 GitHub，而无需在每次访问时提供您的用户名和个人访问令牌 (personal access token)。您还可以使用 SSH 密钥对提交进行签名。
* 设置 SSH 时，您需要生成一个新的私有 SSH 密钥并将其添加到 SSH agent(代理人)。 在使用该密钥对提交进行身份验证或签署之前，您还必须将公共 SSH 密钥添加到您在 GitHub 上的帐户。
### Checking for existing SSH keys
在生成 SSH 密钥之前，您可以检查是否有任何现有的 SSH 密钥。
* 输入 ls -al ~/.ssh 以查看是否存在现有的 SSH 密钥。如果您收到 ~/.ssh 不存在的错误消息，则默认位置中没有现有的 SSH 密钥对。检查目录列表以查看您是否已经拥有公共 SSH 密钥。默认情况下，GitHub 支持的公钥的文件名是以下之一。
```
id_rsa.pub
id_ecdsa.pub
id_ed25519.pub
```
### Generating a new SSH key and adding it to the ssh-agent
检查现有 SSH 密钥后，您可以生成新的 SSH 密钥以用于身份验证，然后将其添加到 ssh-agent。
* 关于 SSH 密钥密码: 您可以在本地计算机上生成新的 SSH 密钥。 生成密钥后，您可以将密钥添加到您在 GitHub.com 上的帐户，以启用通过 SSH 进行 Git 操作的身份验证。
* Generating a new SSH key: 1, 打开终端。. 2, 粘贴下面的文本，替换为您的 GitHub 电子邮件地址。这将使用提供的电子邮件作为标签创建一个新的 SSH 密钥。3, 在提示符处，键入安全密码。
```
ssh-keygen -t ed25519 -C "your_email@example.com"
# -t：指定要创建的密钥类型。-C：添加注释。
123456
```
* Adding your SSH key to the ssh-agent
ssh 推荐的登录方式是使用私钥登录。但是如果生成私钥的时候，设置了口令/密码（passphrase），每次登录时需要输入口令也很麻烦。可以通过 ssh-agent 来管理私钥，把私钥加载进内存，之后便不用再输入密码。1, 在后台启动 ssh-agent. 2, 将您的 SSH 私钥添加到 ssh-agent.
```
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```
### Adding a new SSH key to your GitHub account
要在 GitHub.com 上配置您的帐户以使用新的（或现有的）SSH 密钥，您还需要将密钥添加到您的帐户。
* 关于向您的帐户添加 SSH 密钥: 您可以使用 SSH（安全外壳协议）访问和写入 GitHub.com 上的存储库中的数据。 当您通过 SSH 连接时，您使用本地计算机上的私钥文件进行身份验证。生成 SSH 密钥对后，您必须将公钥添加到 GitHub.com 才能为您的帐户启用 SSH 访问。
* 向您的帐户添加新的 SSH 密钥: 在 GitHub.com 上向您的帐户添加新的 SSH 身份验证密钥后，您可以重新配置任何本地存储库以使用 SSH。1, 将 SSH 公钥复制到剪贴板。2, 在任何页面的右上角，单击您的个人资料照片，然后单击设置。...
```
cat ~/.ssh/id_ed25519.pub
```
### Testing your SSH connection
在您设置 SSH 密钥并将其添加到您在 GitHub.com 上的帐户后，您可以测试您的连接。