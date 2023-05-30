## 在 VBA 中，可以使用 FileSystemObject 对象的 CopyFolder 方法来复制整个文件夹及其内部的所有文件和子文件夹。以下是一个示例代码：
```
Sub CopyFolder(sourceFolderPath As String, destinationFolderPath As String)
    ' 创建 FileSystemObject 对象
    Dim fso As Object
    Set fso = CreateObject("Scripting.FileSystemObject")
    
    ' 复制文件夹及其内容
    fso.CopyFolder sourceFolderPath, destinationFolderPath
    
    ' 释放对象
    Set fso = Nothing
    
    MsgBox "文件夹复制完成。"
End Sub
```
使用示例：
```
Sub ExampleUsage()
    Dim sourceFolder As String
    Dim destinationFolder As String
    
    ' 设置源文件夹和目标文件夹路径
    sourceFolder = "C:\path\to\source\folder"
    destinationFolder = "C:\path\to\destination\folder"
    
    ' 复制文件夹及其内容
    CopyFolder sourceFolder, destinationFolder
End Sub
```