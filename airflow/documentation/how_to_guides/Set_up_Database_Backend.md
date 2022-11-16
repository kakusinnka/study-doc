# Set up a Database Backend
* Airflow 被构建为使用 SqlAlchemy 与其元数据进行交互。
* SQLAlchemy 是 Python SQL 工具包和对象关系映射器，它为应用程序开发人员提供了 SQL 的全部功能和灵活性。 它提供了一整套众所周知的企业级持久性模式，专为高效和高性能的数据库访问而设计，适用于简单的 Python 领域语言。

## 选择数据库后端
如果您想真正体验 Airflow，您应该考虑将数据库后端设置为 PostgreSQL、MySQL 或 MSSQL。 默认情况下，Airflow 使用 SQLite，它仅用于本地开发目的。

## Database URI
* Airflow 使用 SQLAlchemy 连接数据库，这需要您配置 Database URL。 您可以在 [database] 部分的选项 sql_alchemy_conn 中执行此操作。
```
[database]
sql_alchemy_conn = my_conn_string
```
* 使用 AIRFLOW__DATABASE__SQL_ALCHEMY_CONN 环境变量配置此选项也很常见。
```
export AIRFLOW__DATABASE__SQL_ALCHEMY_CONN=my_conn_string
```

## Setting up a SQLite Database
SQLite 数据库可用于运行 Airflow 以用于开发目的，因为它不需要任何数据库服务器（数据库存储在本地文件中）。使用 SQLite 数据库有很多限制（例如，它只适用于 Sequential Executor），它永远不应该用于生产。

## Setting up a PostgreSQL Database

## Setting up a MySQL Database

## Setting up a MsSQL Database

## Other configuration options
您可以指定一个数据库架构，Airflow 将在其中创建所需的表。 如果您希望 Airflow 将其表安装在 PostgreSQL 数据库中，请指定以下环境变量：
```
export AIRFLOW__DATABASE__SQL_ALCHEMY_CONN="postgresql://postgres@localhost:5432/my_database?options=-csearch_path%3Dairflow"
export AIRFLOW__DATABASE__SQL_ALCHEMY_SCHEMA="airflow"
```

## 初始化数据库
在 Airflow 配置中配置数据库并连接到它之后，您应该创建数据库架构。
```
airflow db init
```