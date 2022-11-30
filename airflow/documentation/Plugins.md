# Plugins(插件)
Airflow 内置了一个简单的插件管理器，只需将文件拖放到 $AIRFLOW_HOME/plugins 文件夹中，即可将外部功能集成到其核心中。

## 做什么的？
## 为什么要建立在 Airflow 之上？
## 什么时候（重新）加载插件？
默认情况下，插件是延迟加载的，一旦加载，就永远不会重新加载(except the UI plugins are automatically loaded in Webserver)。要在每个 Airflow 进程开始时加载它们，请在 airflow.cfg 中设置 [core] lazy_load_plugins = False。这意味着如果您对插件进行任何更改并且您希望网络服务器或调度程序使用该新代码，您将需要重新启动这些进程。

## 界面
## 例子
## 关于基于角色的视图的注意事项
## 从 CSRF 保护中排除视图
## 作为 Python 包的插件
## 自动重新加载网络服务器
当检测到带有插件的目录发生更改时，要启用网络服务器的自动重新加载，您应该将 [webserver] 部分中的 reload_on_plugin_change 选项设置为 True

## 故障排除