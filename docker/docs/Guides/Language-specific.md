# Overview
特定语言的入门指南将引导您完成设置开发环境的过程，并开始使用 Docker 对特定语言的应用程序进行容器化。

# Node.js
先放一放

# Python
先放一放

# Java
## 概述
开始使用 Java  
Java 入门指南教您如何使用 Docker 创建容器化的 Spring Boot 应用程序。在本模块中，您将学习如何：

使用 Maven 克隆并运行 Spring Boot 应用程序
创建一个新的 Dockerfile，其中包含构建 Java 映像所需的指令
将新建的镜像作为容器运行
设置本地开发环境以将数据库连接到容器
使用 Docker Compose 运行 Spring Boot 应用
使用 GitHub Actions 为您的应用程序配置 CI/CD 管道
将您的应用程序部署到云端
完成 Java 入门模块后，您应该能够根据本指南中提供的示例和说明将您自己的 Java 应用程序容器化。

让我们开始吧！
## 构建镜像
* 从 github 克隆示例应用程序
* 利用 mvnw 在本地运行项目
* 创建 Dockerfile 遇见一个问题, 说 ./mvnw 不存在 解决办法: ./mvnw 文件中的换行符换成 LF.
  ```
  # syntax=docker/dockerfile:1

  FROM eclipse-temurin:17-jdk-jammy

  WORKDIR /app

  COPY .mvn/ .mvn
  COPY mvnw pom.xml ./
  RUN ./mvnw dependency:resolve

  COPY src ./src

  CMD ["./mvnw", "spring-boot:run"]
  ```
* 创建一个.dockerignore文件
* 用 docker build 命令构建镜像 遇见一个问题 某个依赖报错 解决办法 去掉报错依赖
* 用 docker tag 命令 为镜像文件创建新的标签

## 运行容器
* 用 docker run 命令运行容器
* 用 --publish 标记 简称（-p） 暴漏端口
* 用 --detach 标记 简称（-d）后台运行您的容器
* 列出容器 docker ps
* 停止容器 docker stop
* 重启容器 docker restart
* 删除容器 docker rm
* 要命名容器，我们只需要将 --name 标志传递给 docker run 命令即可
* 容器停止时 并删除容器 docker run --rm

## 开发应用
* docker volume create 创建托管卷
* docker network create 创建桥接网络
* 在容器中运行 MySQL 并附加到我们上面创建的卷和网络
```
docker run -it --rm -d -v mysql_data:/var/lib/mysql \
-v mysql_config:/etc/mysql/conf.d \
--network mysqlnet \
--name mysqlserver \
-e MYSQL_USER=petclinic -e MYSQL_PASSWORD=petclinic \
-e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=petclinic \
-p 3306:3306 mysql:8.0
```
* 运行 APP 容器 并连接到数据库
```
docker run --rm -d \
--name springboot-server \
--network mysqlnet \
-e MYSQL_URL=jdbc:mysql://mysqlserver/petclinic \
-p 8080:8080 java-docker
```

### 多阶段 Dockerfile
* 多阶段 Dockerfile
```
# syntax=docker/dockerfile:1
# 源代码 构建环境
FROM eclipse-temurin:17-jdk-jammy as base
WORKDIR /app
COPY .mvn/ .mvn
COPY mvnw pom.xml ./
RUN ./mvnw dependency:resolve
COPY src ./src

# 运行开发阶段代码
FROM base as development
CMD ["./mvnw", "spring-boot:run", "-Dspring-boot.run.profiles=mysql", "-Dspring-boot.run.jvmArguments='-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:8000'"]

# 打包
FROM base as build
RUN ./mvnw package

# 运行产品阶段代码
FROM eclipse-temurin:17-jre-jammy as production
EXPOSE 8080
COPY --from=build /app/target/spring-petclinic-*.jar /spring-petclinic.jar
CMD ["java", "-Djava.security.egd=file:/dev/./urandom", "-jar", "/spring-petclinic.jar"]
```
* 使用 Compose: Compose 文件非常方便，因为我们不必键入所有参数来传递给docker run命令。我们可以使用 Compose 文件以声明方式执行此操作。
```
version: '3.8'
services:
  petclinic:
    build:
      context: .
      target: development
    ports:
      - "8000:8000"
      - "8080:8080"
    environment:
      - SERVER_PORT=8080
      - MYSQL_URL=jdbc:mysql://mysqlserver/petclinic
    volumes:
      - ./:/app
    depends_on:
      - mysqlserver

  mysqlserver:
    image: mysql:8.0
    ports:
      - "3306:3306"
    environment:
      - MYSQL_ROOT_PASSWORD=
      - MYSQL_ALLOW_EMPTY_PASSWORD=true
      - MYSQL_USER=petclinic
      - MYSQL_PASSWORD=petclinic
      - MYSQL_DATABASE=petclinic
    volumes:
      - mysql_data:/var/lib/mysql
      - mysql_config:/etc/mysql/conf.d
volumes:
  mysql_data:
  mysql_config:
```
### 连接调试器
先放一放

## 运行测试
我们可以通过使用 **RUN** 语句而不是 **CMD** 对测试阶段的语句来稍微改进一下。该 **CMD** 语句不会在镜像构建期间执行，而是在实例容器时执行。使用 **RUN** 语句时，我们的测试会在构建映像时运行，并在构建失败时停止构建。
```
# syntax=docker/dockerfile:1
# 源代码 构建环境
FROM eclipse-temurin:17-jdk-jammy as base
WORKDIR /app
COPY .mvn/ .mvn
COPY mvnw pom.xml ./
RUN ./mvnw dependency:resolve
COPY src ./src

# 运行测试
FROM base as test
RUN ["./mvnw", "test"]

# 运行开发阶段代码
FROM base as development
CMD ["./mvnw", "spring-boot:run", "-Dspring-boot.run.profiles=mysql", "-Dspring-boot.run.jvmArguments='-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:8000'"]

# 打包
FROM base as build
RUN ./mvnw package

# 运行产品阶段代码
FROM eclipse-temurin:17-jre-jammy as production
EXPOSE 8080
COPY --from=build /app/target/spring-petclinic-*.jar /spring-petclinic.jar
CMD ["java", "-Djava.security.egd=file:/dev/./urandom", "-jar", "/spring-petclinic.jar"]
```

## 配置 CI/DI
先放一放

## 部署应用
具体产品，具体学习

# Go
先放一放

# C#(.NET)
先放一放
