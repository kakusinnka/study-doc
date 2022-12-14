# 调试
Visual Studio Code 的主要功能之一是其强大的调试支持。VS Code 的内置调试器有助于加速您的编辑、编译和调试。

## 调试器扩展
## 开始调试
## 运行和调试视图
* 点击 Run and Debug
* 按下 F5
* 使用键盘快捷键 Ctrl+Shift+D

## 运行菜单(Run menu)
## 启动配置
* 创建一个 .vscode 文件夹并将 launch.json 文件添加到您的工作区。
* user settings 或 workspace settings.
* 启动与附加配置
* 添加新配置

## 调试操作
## 断点
## 日志点
Logpoint 是断点的变体，它不会“中断”调试器，而是将消息记录到控制台。Logpoint 由一个“菱形”形状的图标表示。

## 数据检查
## Launch.json 属性
以下属性对于每个启动配置都是必需的：
* type: 此启动配置的调试器类型。
* request: 此启动配置的请求类型。目前支持 launch 和 attach。
* name: 显示在调试启动配置下拉列表中的读者友好名称。

## 变量替换
* ${workspaceFolder} 给出工作区文件夹的根路径
* ${file} 在活动编辑器中打开的文件
* ${env:Name} 环境变量 “Name”。

## 特定于平台的属性
Launch.json 支持根据运行调试器的操作系统定义值。

## 全局启动配置
## 高级断点主题
一个强大的 VS Code 调试功能是能够根据表达式、命中计数或两者的组合设置条件。“命中计数”控制断点在“中断”执行之前需要命中多少次。
* 内联断点: 只有当执行到达与内联断点关联的列时，才会命中内联断点。可以使用 Shift+F9 或在调试会话期间通过上下文菜单设置内联断点。
* 函数断点: 调试器可以支持通过指定函数名称来创建断点，而不是直接在源代码中放置断点。这在源不可用但函数名称已知的情况下很有用。
* 数据断点: 如果调试器支持数据断点，则可以从 VARIABLES 视图设置断点，并在基础变量的值更改时触发断点。

## 调试控制台 REPL(Read-Eval-Print Loop 「读取-求值-输出」循环)
可以使用调试控制台 REPL（读取-评估-打印循环）功能评估表达式。

## 将输入/输出重定向到调试目标/从调试目标重定向
## 多目标调试
* 对于涉及多个进程（例如，客户端和服务器）的复杂场景，VS Code 支持多目标调试。
* 启动多个调试会话的另一种方法是使用复合启动配置。

## 远程调试
## 调试服务器程序时自动打开一个 URI