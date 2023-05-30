## 在 VBA 中，可以通过读取和写入文件来去掉 UTF-8 编码文件的 BOM（字节顺序标记）。以下是一个示例代码：
```
Sub RemoveBOMFromUTF8File(filePath As String)
    Dim content As String
    
    ' 读取文件内容
    Open filePath For Binary Access Read As #1
    content = Space$(LOF(1))
    Get #1, , content
    Close #1
    
    ' 检查文件是否包含 UTF-8 BOM
    If Left$(content, 3) = Chr$(239) & Chr$(187) & Chr$(191) Then
        ' 去掉 BOM
        content = Mid$(content, 4)
        
        ' 将内容写回文件（覆盖原文件）
        Open filePath For Binary Access Write As #1
        Put #1, , content
        Close #1
        
        MsgBox "成功去除 UTF-8 BOM。"
    Else
        MsgBox "文件不包含 UTF-8 BOM。"
    End If
End Sub
```
## 使用示例：
```
Sub ExampleUsage()
    Dim filePath As String
    
    ' 设置文件路径
    filePath = "C:\path\to\filename.txt"
    
    ' 去除文件中的 UTF-8 BOM
    RemoveBOMFromUTF8File filePath
End Sub
```