## 在VBA中，默认情况下，使用的是系统的本地编码格式打开文件。如果您需要使用UTF-8编码格式打开文件，您可以使用ADODB.Stream对象来实现。以下是一个示例代码，演示如何在VBA中使用UTF-8编码格式打开文件：
```
Sub ReadFileWithUTF8Encoding()
    Dim filePath As String
    Dim fileContent As String
    Dim stream As Object

    ' 设置文件路径
    filePath = "C:\path\to\your\file.txt"

    ' 创建 ADODB.Stream 对象
    Set stream = CreateObject("ADODB.Stream")

    ' 配置 ADODB.Stream 对象
    stream.Type = 2 ' 指定为文本数据类型
    stream.Charset = "UTF-8" ' 指定编码为 UTF-8
    stream.Open ' 打开流

    ' 从文件中加载数据到流对象
    stream.LoadFromFile filePath

    ' 将流对象的内容转换为字符串
    fileContent = stream.ReadText

    ' 关闭流
    stream.Close

    ' 输出文件内容
    Debug.Print fileContent
End Sub

```