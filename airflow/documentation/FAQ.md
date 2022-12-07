# 常见问题

## 调度/DAG文件解析
### 为什么任务没有被安排？
您的任务可能无法安排的原因有很多。以下是一些常见原因：
* 确保 Python 文件编译成功
* 包含您的 DAG 的文件是否在内容的某处包含字符串 “airflow” 和 “DAG” ？ 
* 您的 start_date 设置正确吗？ Airflow 调度程序会在 start_date + schedule_interval 过去后立即触发任务。
* 您必须直接为 DAG 对象指定 schedule_interval
* 您的 start_date 是否超出了您在 UI 中可以看到的范围？ 如果您将 start_date 设置为 3 个月前的某个时间，您将无法在 UI 的主视图中看到它，但您应该能够在 Menu -> Browse ->Task Instances 中看到它。
* 是否满足任务的依赖性？ 任务直接上游的任务实例需要处于成功状态。
  * 如果您已设置 depends_on_past=True，则前一个任务实例需要成功（除非它是该任务的第一次运行）。 此外，
  * 如果 wait_for_downstream=True，则紧接在前一个任务实例下游的所有任务都必须成功。
* 您需要的 DagRun 是否已创建并处于活动状态？您可以通过单击 DAG 的计划标签来批量查看 DagRun 和更改状态的列表。
* 你的 DAG 的并发参数达到了吗？ 并发性定义了一个 DAG 允许有多少个正在运行的任务实例，超过这个点就会排队。
* 你的 DAG 的 max_active_runs 参数达到了吗？ max_active_runs 定义允许有多少个正在运行的 DAG 并发实例。
### 如何提高DAG性能？
### 如何降低DAG调度延迟/任务延迟？
### 如何根据另一个任务的失败触发任务？
### 当有很多（>1000）个dags文件时，如何加快新文件的解析？
## DAG构建
### 怎么回事start_date？
### 使用时区
### 是什么execution_date意思？
### 如何动态创建 DAG？
### 是否允许使用顶级 Python 代码？
### 宏是否在另一个 Jinja 模板中解析？
### 为什么next_ds或prev_ds可能不包含预期值？
## 任务执行交互
### 是什么TemplateNotFound意思？
### 如何根据另一个任务的失败触发任务？
## 气流用户界面
### 如何停止每个网络服务器多次发生的同步 perms？
### 如何减少气流 UI 页面加载时间？
### 为什么暂停 dag 切换变成红色？
## MySQL 和 MySQL 变体数据库
### “MySQL Server 已经消失”是什么意思？
### Airflow 是否支持扩展的 ASCII 或 unicode 字符？
### 如何修复异常：全局变量explicit_defaults_for_timestamp需要打开（1）？