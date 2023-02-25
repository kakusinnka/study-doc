# Get started
## 第 1 部分：概述
本指南包含有关如何开始使用 Docker 的分步说明。您将在本指南中学到和做的一些事情是：
* 构建并运行镜像作为容器
* 使用 Docker Hub 共享镜像
* 使用带有数据库的多个容器部署 Docker 应用程序
* 使用 Docker Compose 运行应用程序

## 第 2 部分：容器化应用程序
* 用 git 获取应用程序
* 写一个 Dockerfile, 使用 docker build 构建镜像。
* 使用 docker run 启动容器。

## 第 3 部分：更新应用程序
* 更新代码，重新 build 镜像，停止旧的容器，启动新容器（避免端口冲突）。

## 第 4 部分：共享应用程序
* 创建 Docker Hub
* 使用 docker push 推镜像（注意镜像名前半部分要与远程库匹配）。
* 使用 ddocker run 运行新做的镜像。

## 第 5 部分：保留数据
一个容器中创建的文件在另一个容器中不可用。卷提供了将容器的特定文件系统路径连接回主机的能力。
* 使用 **docker volume create** 命令创建卷（在 Docker Desktop 中运行时，Docker 命令实际上是在您机器上的小型 VM 中运行。如果您想查看挂载点目录的实际内容，则需要查看该 VM 的内部）。
  ```
  docker run -dp 3000:3000 --mount type=volume,src=todo-db,target=/etc/todos getting-started
  ```
* 运行容器时，添加 --mount 指定卷装载的选项。
* 使用 docker volume inspect 命令查看卷的信息。Mountpoint是磁盘上存储数据的实际位置。

## 第 6 部分：使用绑定安装
绑定挂载是另一种类型的挂载，它允许您将主机文件系统中的目录共享到容器中。
```
docker run -it --mount type=bind,src="$(pwd)",target=/src ubuntu bash
```

## 第 7 部分：多容器应用程序
每个容器都应该做一件事，并且把它做好。
* 使用 docker network create 创建网络。

## 第 8 部分：使用 Docker Compose
* 创建一个名为 docker-compose.yml 的文件。
```
services:
  app:
    image: node:18-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:8.0
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```
* 使用 **docker compose up** 命令启动应用程序堆栈。我们将添加-d标志以在后台运行所有内容。

## 第 9 部分：形象构建最佳实践
* 安全扫描: 构建映像后，最好使用 **docker scan** 命令扫描它以查找安全漏洞。
* 镜像分层: 使用 **docker image history ** 命令查看镜像分层。
* 镜像缓存
* 多阶段构建: 1,将构建时依赖与运行时依赖分开. 2, 通过仅传送您的应用程序运行所需的内容来减小整体图像大小.

## 第 10 部分：下一步是什么？