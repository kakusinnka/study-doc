# airflow.models.dag.DAG
dag（有向无环图）是具有方向依赖关系的任务的集合。dag 还有一个时间表、一个开始日期和一个结束日期（可选）。DAG 本质上充当任务的命名空间。task_id 只能添加一次到 DAG。请注意，如果您计划使用时区，则提供的所有日期都应该是 pendulum dates。

## Parameters
* dag_id (str): DAG的id； 必须完全由字母数字字符、破折号、圆点和下划线组成（全部为 ASCII）。
* description (str | None): DAG 的描述，例如 显示在网络服务器上。
* schedule (ScheduleArg)： 定义计划 DAG 运行所依据的规则。可以接受 [cron 字符串](https://crontab.guru/)、timedelta 对象、时间表或数据集对象列表。另请参阅使用时间表自定义 DAG 调度。
* start_date (datetime | None): 调度程序将尝试回填的时间戳。
* end_date (datetime | None)： 您的 DAG 将不会运行的日期，保留为 None 以进行开放式调度。
* catchup (bool): 执行调度程序catchup（或仅运行最新）？ 默认为真。
* tags (list[str] | None)： 帮助过滤 UI 中的 DAG 的标签列表。