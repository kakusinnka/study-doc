# Debian/Ubuntu
在 Debian 和基于 Debian 的发行版（如 Ubuntu）上，您可以通过 apt 安装 Jenkins。

## Long Term Support release 长期支持版本
每 12 周从常规版本流中选择一个 LTS（长期支持）版本作为该时间段的稳定版本。它可以从 debian-stable apt 存储库安装。

## Weekly release 每周发布
每周都会发布一个新版本，以向用户和插件开发人员提供错误修复和功能。 它可以从 debian apt 存储库安装。
### 软件包安装将
* 将 Jenkins 设置为启动时启动的守护进程。 运行 systemctl cat jenkins 以获取更多详细信息。
* 创建一个“jenkins”用户来运行这个服务。
* 直接将控制台日志输出到 systemd-journald。 如果要对 Jenkins 进行故障排除，请运行 journalctl -u jenkins.service。
* 使用启动的配置参数填充 /lib/systemd/system/jenkins.service，例如 JENKINS_HOME
* 将 Jenkins 设置为侦听端口 8080。使用浏览器访问此端口以开始配置。
* 如果 Jenkins 因为某个端口正在使用而无法启动，请运行 systemctl edit jenkins 并添加以下内容：
```
[Service]
Environment="JENKINS_PORT=8081"
```

## Java的安装
Jenkins 需要 Java 才能运行，但某些发行版默认不包含此功能，并且某些 Java 版本与 Jenkins 不兼容。
### 更新 Debian apt 存储库，安装 OpenJDK 11，并使用以下命令检查安装：

## 自己的安装记录
* 安装后访问 8080 端口, 获得初始密码进行登录, 顺带安装推荐插件, 创建第一个管理员用户。
```
sudo apt update
sudo apt install openjdk-11-jre
java -version

curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update
sudo apt-get install jenkins
```

