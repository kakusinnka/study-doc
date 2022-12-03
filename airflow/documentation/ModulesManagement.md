# 模块管理
Airflow 允许您在 DAG 和 Airflow 配置中使用自己的 Python 模块。

## Python 中的包/模块加载是如何工作的
Python 尝试从中加载模块的目录列表由变量 sys.path 给出。
```
>>> import sys
>>> from pprint import pprint
>>> pprint(sys.path)
['',
 '/home/arch/.pyenv/versions/3.7.4/lib/python37.zip',
 '/home/arch/.pyenv/versions/3.7.4/lib/python3.7',
 '/home/arch/.pyenv/versions/3.7.4/lib/python3.7/lib-dynload',
 '/home/arch/venvs/airflow/lib/python3.7/site-packages']
```

## 包的典型结构
这是您的 dags 文件夹中可能有的示例结构:
```
<DIRECTORY ON PYTHONPATH>
| .airflowignore  -- only needed in ``dags`` folder, see below
| -- my_company
              | __init__.py
              | common_package
              |              |  __init__.py
              |              | common_module.py
              |              | subpackage
              |                         | __init__.py
              |                         | subpackaged_util_module.py
              |
              | my_custom_dags
                              | __init__.py
                              | my_dag1.py
                              | my_dag2.py
                              | base_dag.py
```
在上述情况下，这些是您可以导入 python 文件的方法:
```
from my_company.common_package.common_module import SomeClass
from my_company.common_package.subpackge.subpackaged_util_module import AnotherClass
from my_company.my_custom_dags.base_dag import BaseDag
```

## Airflow 中的内置 PYTHONPATH 条目
* dags 文件夹：它在 [core] 部分配置了选项 dags_folder
* config 文件夹：默认情况下，它通过设置 AIRFLOW_HOME 变量 ({AIRFLOW_HOME}/config) 进行配置。
* plugins 文件夹：它在 [core] 部分配置了选项 plugins_folder。

## 模块加载的最佳实践
### 使用唯一的顶级包名称
* 建议您始终将文件放在您所独有的子包中
### 不要使用相对导入
* 切勿使用 Python 3 中添加的相对导入
### 在包文件夹中添加 __init__.py
* 创建文件夹时，您应该将__init__.py文件作为空文件添加到文件夹中。虽然在 Python 3 中有一个隐式命名空间的概念，您不必将这些文件添加到文件夹中，但 Airflow 期望这些文件被添加到您添加的所有包中。

## 检查您的 PYTHONPATH 加载配置
您还可以使用 airflow info 命令查看确切路径，并使用它们类似于使用环境变量 PYTHONPATH 指定的目录。

## 将目录添加到 PYTHONPATH
## 在 Python 中创建包