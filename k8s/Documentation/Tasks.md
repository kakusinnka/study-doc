# 任务
## 安装工具
### kubectl
Kubernetes 命令行工具 kubectl， 让你可以对 Kubernetes 集群运行命令。 你可以使用 kubectl 来部署应用、监测和管理集群资源以及查看日志。
### 在 Linux 上安装 kubectl: 
1. 实例化一台 GCE 虚拟机。
2. 安装 Dokcer。
```
https://techviewleo.com/install-use-docker-desktop-on-debian/
$ sudo apt update -y && sudo apt upgrade -y

$ sudo modprobe kvm
$ sudo modprobe kvm_intel
$ lsmod | grep kvm
$ ls -al /dev/kvm

$ sudo rm -r $HOME/.docker/desktop
$ sudo rm /usr/local/bin/com.docker.cli
$ sudo apt purge docker-desktop

$ sudo apt install gnome-terminal
$ sudo apt install ca-certificates curl gnupg software-properties-common lsb-release  -y
$ curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
$ sudo apt update -y
$ sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin
$ sudo usermod -aG docker $USER
$ newgrp docker
$ sudo apt-get install wget
$ wget https://desktop.docker.com/linux/main/amd64/docker-desktop-4.12.0-amd64.deb
$ sudo apt install ./docker-desktop-*-amd64.deb 
$ sudo vim /etc/hosts
$ docker version
$ systemctl --user start docker-desktop
$ systemctl --user status docker-desktop
$ docker ps
```
3. minikube 启动
```
$ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
$ sudo dpkg -i minikube_latest_amd64.deb
$ minikube start
```
4. 在 Linux 上安装 kubectl。
```
用原生包管理工具安装(基于 Debian 的发行版):
1. 更新 apt 包索引并使用 Kubernetes apt 存储库安装所需的包：
  sudo apt-get update
  sudo apt-get install -y ca-certificates curl
2. 下载 Google Cloud 公开签名秘钥：
  sudo mkdir /etc/apt/keyrings
  sudo curl -fsSLo /etc/apt/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
3. 添加 Kubernetes apt 仓库：
  echo "deb [signed-by=/etc/apt/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
4. 更新 apt 包索引，使之包含新的仓库并安装 kubectl：
  sudo apt-get update
  sudo apt-get install -y kubectl
```
### 验证 kubectl 配置
```
kubectl cluster-info
```