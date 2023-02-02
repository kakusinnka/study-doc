# Overview
特定语言的入门指南将引导您完成设置开发环境的过程，并开始使用 Docker 对特定语言的应用程序进行容器化。

# Node.js

# Python

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

# Go

# C#(.NET)