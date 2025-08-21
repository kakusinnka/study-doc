## 知道 Django 是否已安装以及安装的版本
```python
py -m django --version
```

## 运行以下命令启动一个新的 Django 项目
```python
# 这将在 djangotutorial 目录中创建一个名为 mysite 的项目。
django-admin startproject mysite djangotutorial
```

## 要创建应用程序，请确保与 manage.py 位于同一目录，然后键入以下命令
```python
py manage.py startapp polls
```

## 通过运行 makemigrations ，您可以告诉 Django，您对模型进行了一些更改，并且您希望将这些更改存储为迁移。
```python
python manage.py makemigrations polls
```

## 看看迁移会运行哪些 SQL
```python
python manage.py sqlmigrate polls 0001
```

## 检查项目中的任何问题，而无需进行迁移或接触数据库。
```python
# 用于检测项目中的问题。它会检查项目的配置、模型、数据库设置以及其他潜在问题，但不会对数据库进行任何操作。
python manage.py check
```

## 应用迁移文件
```python
# 应用迁移文件，将模型定义同步到数据库。
# 初始化数据库结构，创建默认应用的表。
# 管理迁移状态，确保迁移不会重复执行。
python manage.py migrate
```

## 启动一个交互式 shell，加载 Django 项目环境。
```python
# python manage.py shell 的作用：
# 启动一个交互式 shell，加载 Django 项目环境。
# 提供对模型、数据库、配置等的直接访问。

# 常见操作：
# 导入模型。
# 查询、创建、更新、删除数据库记录。
# 测试项目的其他组件。
python manage.py shell
```

## 单元测试的命令
```python
# Django 会创建一个临时的测试数据库。
# Django 会扫描 polls 应用的代码目录，寻找以 test 开头的文件（例如 tests.py）。
# Django 会运行测试类中定义的每个测试方法。
# Django 会输出测试结果，包括成功的测试数量、失败的测试数量以及详细的错误信息（如果有）。
py manage.py test polls
```

## 运行 Django 项目
```python
py manage.py runserver
```

## 创建超级用户
```python
python manage.py createsuperuser
```

## 导入 JSON 数据
```python
# Django 的 loaddata 会在事务中运行。如果导入过程中发生错误，所有更改都会回滚，确保数据库一致性。
# 如果 JSON 文件中包含的字段在模型中不存在，可以使用 --ignorenonexistent 参数忽略这些字段。
# Django 使用 pk（主键）来判断数据是否已经存在。
# 如果 JSON 文件中的数据的 pk 在数据库中已经存在，则会尝试更新该记录。
# 如果 pk 不存在，则会创建新的记录。
python manage.py loaddata data.json
```

## connection.queries 属性，可以用来捕获所有执行的 SQL 查询。
```python
from django.db import connection

print(connection.queries[-1]["sql"]) # 打印最后一条 SQL 查询
```