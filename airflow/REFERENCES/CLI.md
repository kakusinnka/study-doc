# CLI
## Command Line Interface
Airflow 有一个非常丰富的命令行界面，允许对 DAG 进行多种类型的操作，启动服务，支持开发和测试。
## Environment Variables
在 Airflow 配置中设置选项。 这优先于 airflow.cfg 文件中的值。将 {SECTION} 占位符替换为任何部分，并将 {KEY} 占位符替换为该指定部分中的任何键。例如，如果你想在 [core] 部分设置 dags_folder 选项，那么你应该设置 AIRFLOW__CORE__DAGS_FOLDER 环境变量。  
有关详细信息，请参阅：[设置配置选项](https://airflow.apache.org/docs/apache-airflow/2.2.5/howto/set-config.html)。