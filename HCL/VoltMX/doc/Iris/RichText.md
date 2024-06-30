# RichText 富文本
使用 RichText 小组件显示格式化文本。“富文本”小组件使用 HTML 格式标记来显示带有链接、图像和字符样式（如粗体和斜体）的文本。

## 重要考虑因素
如果为 RichText 构件指定外观，则字体级别设置（如颜色样式和大小）将应用于构件的整个内容。使用标签样式 HTML 格式标记覆盖外观指定的文本颜色。

## Look Properties Look 属性
略

## Skin Properties 皮肤特性
* Normal 正常: 小组件的默认外观。
* Link 链接: 应用于 RichText 小组件中的链接的外观。
* Link Focus 链接焦点: 当皮肤具有焦点时应用于链接。
* Telephone Link 电话链接: 应用于 RichText 小组件中的电话链接的外观。> 注意：Telephone Link 外观仅在 Windows 平台上可用。
* Hover 悬停: 光标悬停在小组件上时小组件的外观。> 注意：悬停皮肤仅在 Windows（本机）平板电脑平台上可用。
* Super Script 超级脚本: 应用于 RichText 小组件中上标的外观。> 注意：Super Script 皮肤仅在 Windows 平台上可用。

## Rich Text Properties
### Rich Text Wrapping 富文本换行
指定标签如何换行文本，即“自动换行”或“自动换行”：
* 自动换行（默认）：行尾的单词之间的文本自动换行。
* 字符换行：行尾字符之间的文本换行。

### Tool Tip 工具提示
对于 Windows 平板电脑平台，指定将鼠标指针悬停在小组件上时显示的消息。

## Actions 行动
* onClick：当用户单击小组件时触发操作。
* onTouchStart：当用户触摸触摸表面时触发操作。此事件以异步方式发生。
* onTouchMove：当触摸在触摸表面上连续移动直到移动结束时，将触发该操作。此事件以异步方式发生。
* onTouchEnd：当用户触摸从触摸表面释放时触发操作。此事件以异步方式发生。