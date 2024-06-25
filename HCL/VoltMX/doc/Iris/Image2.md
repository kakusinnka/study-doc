# Image 图像
使用“图像”小组件以 PNG、JPEG、GIF 或 WebP 格式显示图形图像，例如公司徽标、照片或插图。

## 重要考虑因素
* 在项目中使用图像之前，请将图像复制到项目子文件夹。有关详细信息，请参[阅添加和管理图像和其他媒体](./AddAndManageImagesAndOtherMedia.md)。
* 在 Android 设备上，在功能预览期间会忽略从可绘制对象文件夹导入的图像。
* 图像文件名必须仅包含小写字符和数字，必须以字母字符开头，并且不能是 JavaScript 保留的单词或关键字。

## Look 属性
略

## Skin Properties 皮肤特性
对于“图像”小组件，您可以将外观及其关联属性应用于以下状态：正常，悬停。

## Image Properties 图像属性
* Scale Mode 缩放模式: 指定如何在“图像”构件中缩放图像。
* 指定要显示的图像的来源。您可以指定 Resources 文件夹中的图像或图像 URL。
* Downloading Image 下载图片: 指定下载远程源时显示的图像。
* Failed Image 失败的映像: 指定远程资源不可用时要显示的图像。
* Tool Tip 工具提示: 对于 Windows 平板电脑平台，指定将鼠标指针悬停在小组件上时显示的消息。

## Actions 行动
* onDownloadComplete：镜像下载完成后触发操作。
* onTouchStart：当用户触摸触摸表面时触发操作。此事件以异步方式发生。
* onTouchMove：当触摸在触摸表面上连续移动直到移动结束时，将触发该操作。此事件以异步方式发生。
* onTouchEnd：当用户触摸从触摸表面释放时触发操作。此事件以异步方式发生。