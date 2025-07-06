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

## 运行 Django 项目
```python
py manage.py runserver
```