# Installation
* Using released sources  
  如果您希望从源代码构建所有软件，则此选项是最佳选择。您负责设置数据库、使用数据库命令创建和管理数据库架构、自动启动和恢复、维护、清理和升级气流和气流提供程序。

* Using PyPI  
  当您不熟悉 Containers 和 Docker 并希望在物理机或虚拟机上安装 Apache Airflow 并且您习惯于使用自定义部署机制安装和运行软件时，这种安装方法非常有用。熟悉安装和配置 Python 应用程序、管理 Python 环境、依赖项和使用自定义部署机制运行软件的用户。 -> Installation_from_PyPI.md

* Using Production Docker Images  
  当您熟悉 Container/Docker 堆栈时，此安装方法很有用。 它提供了将 Airflow 组件与运行在相同物理或虚拟机上的其他软件隔离开来的能力，并且易于维护依赖关系。

* Using Official Airflow Helm Chart  
  当您不仅熟悉 Container/Docker 堆栈，而且当您使用 Kubernetes 并希望通过 Helm chart 使用社区管理的 Kubernetes 安装机制来安装和维护 Airflow 时，这种安装方法非常有用。

* Using Managed Airflow Services  
  当您希望让其他人为您管理 Airflow 安装时，您可以使用托管 Airflow 服务。
  [Cloud Composer](https://cloud.google.com/composer)

* Using 3rd-party images, charts, deployments  
  如果之前提到的官方方法都不适合您，或者您曾经使用过这些安装方法，那么这些安装方法很有用。