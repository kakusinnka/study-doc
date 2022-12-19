# 等待不同的 DAG 或不同 DAG 中的任务完成特定的 execution_date.
## 参数
* external_dag_id: 您要等待的任务的 dag_id.
* external_task_id: 您要等待的任务的 task_id. 如果是 None（默认值）传感器等待 DAG.
* allowed_states: 允许状态列表.
* execution_delta: 