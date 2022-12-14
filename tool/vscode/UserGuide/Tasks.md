# 通过任务与外部工具集成
很多工具提供可以自动执行的任务，例如：检查、构建、打包、测试或部署软件系统。能够在 VS Code 中运行工具并分析它们的结果是很有帮助的。这是 Task 就派上了用场。

## TypeScript Hello World
让我们从一个简单的TypeScript “Hello World” 程序开始，我们要将其编译为 JavaScript。

* 运行任务: 按 Ctrl+Shift+B 或从全局终端菜单运行 Run Build Task.
* 您还可以将 TypeScript 构建或监视任务定义为默认构建任务，以便在触发 Run Build Task (Ctrl+Shift+B) 时直接执行。

## 任务自动检测
VS Code 当前自动检测以下系统的任务：Gulp、Grunt、Jake 和 npm。需要从全局菜单执行运行任务。

## 自定义任务
也就是自定义 task.json 文件:
* label: 用户界面中使用的任务标签
* type: 任务的类型
* command: 要执行的实际命令
* windows: 任何 Windows 特定属性
* group: 定义任务属于哪个组
* presentation: 定义任务输出在用户界面中的处理方式
* options: 覆盖 cwd（当前工作目录）、env（环境变量）或 shell（默认 shell）的默认值
* runOptions: 定义任务运行的时间和方式
### 复合任务
您还可以使用 **dependsOn** 属性将简单的任务进行组合。
### 用户级任务
您可以使用 **Tasks: Open User Tasks** 命令创建不依赖于特定工作区或文件夹的用户级任务。

## 输出行为
有时您想要控制集成终端面板在运行任务时的行为方式。例如，您可能希望最大化编辑器空间并且仅在您认为存在问题时才查看任务输出。可以使用任务的 **presentation** 属性来控制终端的行为。

## 运行行为
您可以使用 **runOptions** 属性指定任务的运行行为: 
* reevaluateOnRerun ：是否在重新运行时重新评估任务变量。
* runOn: 指定何时运行任务。

## 自定义自动检测的任务
## 使用问题匹配器处理任务输出
VS Code 可以使用问题匹配器处理任务的输出。问题匹配器扫描任务输出文本以查找已知警告或错误字符串，并在编辑器和“问题”面板中内联报告这些内容。

## 将键盘快捷键绑定到任务
如果您需要经常运行某个任务，您可以为该任务定义一个键盘快捷键。

## 变量替换
在创作任务配置时，拥有一组预定义的公共变量很有用，例如活动文件 {file} 或工作区根文件夹 {workspaceFolder}。VS Code 支持 tasks.json 文件中字符串内的变量替换，您可以在 **[变量参考](https://code.visualstudio.com/docs/editor/variables-reference)** 中看到预定义变量的完整列表。

## 操作系统特定属性
任务系统支持定义特定于操作系统的值（例如，要执行的命令）。

## 更改任务输出的编码
## 行动中的任务示例
## 定义问题匹配器
## 定义多行问题匹配器
## 修改现有问题匹配器
## 后台/观看任务
