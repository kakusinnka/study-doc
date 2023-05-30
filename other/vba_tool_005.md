## 在 VBA 中，你可以使用 CreateObject("ADODB.Stream") 对象来以 UTF-8 编码格式将内容写入文件。
```
Sub WriteToFile()
    Dim content As String
    Dim filePath As String
    
    ' 设置要写入的内容
    content = "你要写入文件的内容"
    
    ' 设置文件路径
    filePath = "C:\path\to\filename.txt"
    
    ' 创建 ADODB.Stream 对象
    Dim stream As Object
    Set stream = CreateObject("ADODB.Stream")
    
    ' 设置流对象的属性
    stream.Charset = "UTF-8"
    stream.Open
    stream.WriteText content
    
    ' 保存内容到文件
    stream.SaveToFile filePath, 2 ' 2 表示保存为文本文件
    
    ' 关闭流对象
    stream.Close
End Sub
```