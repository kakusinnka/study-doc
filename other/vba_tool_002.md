## 要在VBA中读取文件内容，您可以使用Open语句和Input函数来打开并逐行读取文件。以下是一个示例代码，演示如何在VBA中读取文本文件的内容：
```
Sub ReadFileContent()
    Dim filePath As String
    Dim fileContent As String
    Dim fileLine As String
    Dim fileNumber As Integer
    
    ' 设置文件路径
    filePath = "C:\path\to\your\file.txt"
    
    ' 打开文件以供读取
    fileNumber = FreeFile
    Open filePath For Input As fileNumber
    
    ' 逐行读取文件内容
    Do Until EOF(fileNumber)
        Line Input #fileNumber, fileLine
        fileContent = fileContent & fileLine & vbCrLf
    Loop
    
    ' 关闭文件
    Close fileNumber
    
    ' 在Immediate窗口中输出文件内容
    Debug.Print fileContent
End Sub

```