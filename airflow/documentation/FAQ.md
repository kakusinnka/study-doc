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
有一些 Airflow 配置允许更大的调度容量和频率：
* 并行性(parallelism)这定义了可以在 Airflow 中同时运行的任务实例的最大数量。
* max_active_tasks_per_dag: 每个 DAG 中允许并发运行的最大任务实例数。
* max_active_runs_per_dag: 每个 DAG 运行的活动 DAG 的最大数量。
算子或任务也有提高效率和调度优先级的配置：
* max_active_tis_per_dag: 此参数控制每个任务跨 dag_runs 并发运行的任务实例数。
* pool
* priority_weight
* queue
### 如何降低DAG调度延迟/任务延迟？
Airflow 2.0 具有开箱即用的低 DAG 调度延迟（特别是与 Airflow 1.10.x 相比时），但是如果您需要更高的吞吐量，您可以启动多个调度程序。
### 如何根据另一个任务的失败触发任务？
您可以使用触发规则(trigger_rule)来实现这一点。
### 当有很多（>1000）个dags文件时，如何加快新文件的解析？
将 file_parsing_sort_mode 更改为 modified_time，将 min_file_process_interval 提高到 600（10 分钟）、6000（100 分钟）或更高的值。如果文件最近被修改，dag 解析器将跳过 min_file_process_interval 检查。
## DAG构建
### 怎么回事start_date？
创建新的 DAG 时，您可能希望为您的任务设置一个全局开始日期。 这可以通过直接在 DAG() 对象中声明 start_date 来完成。
### 使用时区
创建时区感知日期时间（例如 DAG 的 start_date）非常简单。 只需确保使用钟摆提供时区感知日期。
### 是什么 execution_date 意思？
* Execution date 或 execution_date 是所谓的 logical date 的历史名称，通常也是 DAG 运行数据间隔的开始。
* Airflow 是作为满足 ETL 需求的解决方案而开发的。 在 ETL 世界中，您通常会汇总数据。 因此，如果您想要汇总 2016-02-19 的数据，您可以在 2016-02-20 午夜 UTC 进行，也就是 2016-02-19 的所有数据可用之后。 2016-02-19 和 2016-02-20 午夜之间的这个间隔称为数据间隔，由于它代表 2016-02-19 日期的数据，因此该日期也称为运行的逻辑日期，或 Execution date。
### 如何动态创建 DAG？
* Airflow 在您的 DAGS_FOLDER 中查找在其全局命名空间中包含 DAG 对象的模块，并将它找到的对象添加到 DagBag 中。 知道了这一点，我们所需要的只是一种在全局命名空间中动态分配变量的方法。 这在 python 中使用标准库的 globals() 函数很容易完成，它的行为就像一个简单的字典。
* 尽管 Airflow 支持每个 python 文件有多个 DAG 定义，动态生成或以其他方式生成，但不推荐这样做，因为 Airflow 希望从故障和部署的角度更好地隔离 DAG，而同一文件中的多个 DAG 违背了这一点。
### 是否允许使用顶级 Python 代码？
虽然不建议在定义 Airflow 结构之外编写任何代码，但 Airflow 确实支持任意 Python 代码，只要它不会破坏 DAG 文件处理器或将文件处理时间延长到超过 dagbag_import_timeout 值。
### 宏是否在另一个 Jinja 模板中解析？
### 为什么 next_ds 或 prev_ds 可能不包含预期值？
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
如果您打算在 Airflow 中使用扩展的 ASCII 或 Unicode 字符，则必须向 MySQL 数据库提供正确的连接字符串，因为它们明确定义了字符集。
### 如何修复异常：全局变量explicit_defaults_for_timestamp需要打开（1）？