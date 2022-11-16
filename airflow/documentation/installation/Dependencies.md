# Dependencies
* Airflowextra dependencies [额外依赖](https://airflow.apache.org/docs/apache-airflow/stable/extra-packages-ref.html)  
  apache-airflow PyPI 基本包仅安装开始所需的内容。根据在您的环境中有用的内容，可以安装其他软件包。
* Provider packages [提供程序包](https://airflow.apache.org/docs/apache-airflow-providers/index.html)  
  Apache Airflow 2 以模块化方式构建。 Apache Airflow 的“核心”提供了核心调度程序功能，允许您编写一些基本任务，但是可以通过安装称为提供程序的附加包来扩展 Apache Airflow 的功能。
* Differences between extras and providers  
  Extras 是标准的 Python setuptools 功能，允许将附加的依赖项集作为可选功能添加到“核心”Apache Airflow。此类可选功能的一种类型是提供程序包，但并非 Apache Airflow 的所有可选功能都有相应的提供程序。
* System dependencies  
  您需要特定的系统级别要求才能安装 Airflow。