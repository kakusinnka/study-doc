# RadioButtonGroup （单选按钮组）
当用户只能选择一个选项时，使用 RadioButtonGroup 小组件从一组单选按钮中进行选择。

## 重要考虑因素
* RadioButtonGroup 小组件始终是组小组件。
* 如果可能的选择数量有限，并且只能进行一个选择，请使用 RadioButtonGroup 小组件。如果可以从组中进行多个选择，请使用 CheckBoxGroup 小组件。若要显示所选内容列表，请使用 ListBox 小组件。
* 如果将 Orientation 属性设置为水平，则不要在组中放置两个以上的项目。如果放置两个以上的项目，并且关联的文本很大，则其他项目可能不适合屏幕宽度，并且不可见。

## Look Properties Look 属性
略

## Skin Properties 皮肤特性
略

## RadioButtonGroup 属性
### Master Data 主数据
指定必须显示的一组值，以便用户从可用选项中进行选择。

### Selected Image 所选图像
指定进行选择时要显示的图像。

### Unselected Image 未选择的图像
指定清除所选内容时要显示的图像。

### Orientation 取向
指定单选按钮的对齐方式是水平对齐还是垂直对齐。

### View Type 视图类型
对于 iOS 平台，指定 RadioButtonGroup 的视图类型，即“列表”、“表”、“切换”或“屏幕滚轮”。

### Drop Down Image 下拉图像
如果视图类型为“列表”，则指定用于下拉框指示器的图像。默认值为倒三角形。

### Group Cells 组单元格
如果视图类型为“表”，则指定是否应用“单元格组”样式。“组单元格”样式对单选按钮组中的项目进行分组。

### View Style 视图样式
如果视图类型为“切换”，则指定切换按钮的视图样式，即“普通”、“边框”或“条形”。

### Equal Segments 相等段
如果视图类型为 Toggle，则指定是否按相等比例分布区段。

### Enable Tint Color 启用色调颜色
如果视图类型为“切换”，则指定是否启用色调颜色。

### Tint Color 色调颜色
如果启用了色调颜色，则指定色调颜色。若要选择色调颜色，请单击颜色选取器以打开颜色选择对话框，然后选择一种颜色。

### Tool Tip 工具提示
对于 Windows 平板电脑平台，指定将鼠标指针悬停在小组件上时显示的消息。

## Actions 行动
* onSelection：选择项目时触发操作。
* onTouchStart：当用户触摸触摸表面时触发操作。此事件以异步方式发生。
* onTouchMove：当触摸在触摸表面上连续移动直到移动结束时，将触发该操作。此事件以异步方式发生。
* onTouchEnd：当用户触摸从触摸表面释放时触发操作。此事件以异步方式发生。