# Installation from PyPI
本页介绍了使用 PyPI 中发布的 apache-airflow 包进行的安装。[PyPI apache-airflow](https://pypi.org/project/apache-airflow/)

* Installation tools  
  目前官方只支持 pip 安装。
* Constraints files  
  Airflow 安装有时会很棘手，因为 Airflow 既是库又是应用程序。为了有一个可重复的安装，我们保留了一组经过测试和工作的依赖项。  
  还有一个 constraints-no-providers 约束文件，其中仅包含安装 Airflow 核心所需的约束。 这允许独立于供应商单独安装和升级气流。
* Installation and upgrade  
  为了简化安装，我们准备了如何升级 Airflow 和提供程序的示例。1，安装 Airflow时附加功能和提供程序。2，与供应商一起升级 Airflow。3，与 Airflow 核心分开安装/升级/降级提供程序。4，Airflow核心安装升级。