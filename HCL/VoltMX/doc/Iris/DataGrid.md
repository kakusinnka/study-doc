# DataGrid 数据网格
使用 DataGrid 小组件以行和列（表格格式）显示数据集合。DataGrid 小组件支持常见的表格式设置选项，例如交替行背景颜色、自定义网格线以及隐藏或显示标题的功能。

## 重要考虑因素
以下是 DataGrid 小组件的重要注意事项。
* 若要设置数据，请首先使用 Data 属性指定行和列。
* 如果 DataGrid 支持“多选”属性，请确保指定“行 - 焦点”属性。否则，您将无法区分多个选择。

## Look 属性
略

## Skin Properties 皮肤特性
* Header 页眉: 应用于“标题”行的外观。
* Row: 当行没有焦点时应用的外观。
* Row - Alternate 行 - 备用: 应用于交替行的外观。
* Row - Focus 行 - 焦点: 当行具有焦点时应用的皮肤。
* Hover Skin 悬停皮肤: 光标悬停在小组件上时小组件的外观。> 注意：悬停皮肤仅在 Windows（本机）平板电脑平台上可用。

## DataGrid Properties
* Data 数据: 表示数据网格的每个单元格中显示的数据。
* Multi-Select 多选: 指定是否可以选择 DataGird 的多行。“行 - 焦点”外观将应用于选定的行。
* Column Headers 列标题: 指定 DataGrid 列标题的可见性。
* Grid Line Color 网格线颜色: 指定网格线的颜色。
* Tool Tip 工具提示: 对于 Windows 平板电脑平台，指定将鼠标指针悬停在小组件上时显示的消息。

## Actions 行动
* onRowSelected：选择行时触发操作。
* onTouchStart：当用户触摸触摸表面时触发操作。此事件以异步方式发生。
* onTouchMove：当触摸在触摸表面上连续移动直到移动结束时，将触发该操作。此事件以异步方式发生
* onTouchEnd：当用户触摸从触摸表面释放时触发操作。此事件以异步方式发生。