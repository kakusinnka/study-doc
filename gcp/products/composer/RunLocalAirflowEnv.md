# 使用 Composer 本地开发 CLI 工具运行本地 Airflow 环境
本部分介绍如何使用 Composer Local Development CLI 工具创建、配置和运行本地 Airflow 环境。

## Composer 本地开发 CLI 工具简介
* Composer Local Development CLI 工具通过在本地运行 Airflow 环境来简化 Cloud Composer 2 的 Apache Airflow DAG 开发。此本地 Airflow 环境使用特定 Cloud Composer 版本的映像。
* 您可以基于现有的 Cloud Composer 环境创建本地 Airflow 环境。在这种情况下，本地 Airflow 环境会从您的 Cloud Composer 环境中获取已安装 PyPI 软件包和环境变量的名称列表。

## 准备工作
* 创建环境目录: 本地环境的所有数据均存储在您创建本地环境的路径下的子目录中.
* 安装 Composer 本地开发 CLI 工具依赖项: Python 3.7 - 3.10（含 pip）. Google Cloud CLI.
* 安装 Docker

## 配置凭据
* 获取用于应用默认凭据的新用户凭据
```
gcloud auth application-default login
```
* 使用您的 Google 帐号登录 gcloud CLI
```
gcloud auth login
```
Composer 本地开发 CLI 工具和 DAG 执行的所有 API 调用均通过您在 gcloud CLI 中使用的帐号执行。

## 安装 Composer 本地开发 CLI 工具
* 克隆 Composer 本地开发 CLI 代码库:
```
git clone https://github.com/GoogleCloudPlatform/composer-local-dev.git
```
* 在克隆代码库的顶级目录中，运行以下命令
```
pip install .
```

## 使用特定 Cloud Composer 版本创建本地 Airflow 环境
```
composer-dev create ^
  --from-image-version composer-2.0.32-airflow-2.3.4 ^
  hzh-local-environment
```

## 通过 Cloud Composer 环境创建本地 Airflow 环境
```
composer-dev create hzh-local-environment2 ^
  --from-source-environment hzh-composer ^
  --location asia-northeast1 ^
  --project my-project-29437-364300 ^
  --port 8089
```

## 启动本地 Airflow 环境
```
composer-dev start hzh-local-environment2
```

## 停止或重启本地 Airflow 环境
当您重启本地 Airflow 环境时，Composer Local Development CLI 工具会重启运行该环境的 Docker 容器。所有 Airflow 组件都将停止并再次启动。因此，在重启期间执行的所有 DAG 运行都会被标记为失败。
```
# 重启
composer-dev restart hzh-local-environment2
# 停止
composer-dev stop hzh-local-environment2
```

## 添加和更新 DAG
## 查看本地 Airflow 环境日志
您可以查看运行本地 Airflow 环境的 Docker 容器中的近期日志。通过这种方式，您可以监控容器相关事件，并检查 Airflow 日志是否存在错误。
```
composer-dev logs hzh-local-environment2 --max-lines 10
```

## 运行 Airflow CLI 命令
```
composer-dev run-airflow-cmd hzh-local-environment2 dags list -o table
```

## 配置本地 Airflow 环境
Composer 本地开发 CLI 工具会将本地 Airflow 环境的配置参数存储在本地环境的目录, 系统会在启动本地 Airflow 环境时应用配置。
### 获取本地 Airflow 环境的列表和状态
```
# 环境列表
composer-dev list
# 特定环境描述
composer-dev describe hzh-local-environment2
```
### 列出本地 Airflow 环境使用的镜像
```
docker images --filter=reference='*/cloud-airflow-releaser/*/*'
```
### 安装插件和更改数据
### 配置环境变量
如需配置环境变量，请修改环境目录中的 variables.env 文件。variables.env 文件必须包含键值对定义，每个环境变量占一行。如需更改 Airflow 配置选项，请使用 AIRFLOW__SECTION__KEY 格式。重启本地 Airflow 环境。
```
# variables.env
ANOTHER_VARIABLE=hzhtest
# python 获取环境变量
import os
foo = os.environ["ANOTHER_VARIABLE"]
```
### 安装或移除 PyPI 软件包
如需安装或移除 PyPI 软件包，请修改环境目录中的 requirements.txt 文件。重启本地 Airflow 环境。
### 切换到其他 Cloud Composer 映像
修改本地环境配置文件 config.json。更改 composer_image_version 参数的值。重启本地 Airflow 环境。
### 删除本地 Airflow 环境
1. 停止本地 Airflow 环境:
```
composer-dev stop hzh-local-environment2
```
2. 删除环境的目录 
### 删除 Docker 映像
```
docker rmi $(docker images --filter=reference='*/cloud-airflow-releaser/*/*' -q)
```