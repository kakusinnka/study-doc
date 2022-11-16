# Jib
![Jib](../images/jib-build-docker-java-container-image.png "Jib")
## What is Jib?
Jib 为您的 Java 应用程序构建优化的 Docker 和 OCI 镜像，而无需 Docker 守护程序。
## Goals
* Fast：只需部署更改的层即可。
* 可重现：用相同的内容重建你的容器镜像总是会生成相同的镜像。
* 无守护进程：从 Maven 或 Gradle 中构建您的 Docker 映像，然后推送到您选择的任何Registry。 不再编写 Dockerfile 和调用 docker build/push。

## Quickstart
## Examples
## How Jib Works
传统上，Java 应用程序是使用应用程序 JAR 作为单个映像层构建的，而 Jib 的构建策略将 Java 应用程序分成多个层，以进行更精细的增量构建。 当您更改代码时，只会重建您的更改，而不是整个应用程序。 默认情况下，这些层位于 OpenJDK 基础镜像之上，但您也可以配置自定义基础镜像。