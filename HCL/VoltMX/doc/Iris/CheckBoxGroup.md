# CheckBoxGroup CheckBox组
当用户可以进行一个或多个选择时，使用 CheckBoxGroup 小组件从一组复选框中进行选择。复选框内的复选标记指示所选内容。

## 重要考虑因素
以下是 CheckBoxGroup 小组件的重要注意事项：
* CheckBoxGroup 小组件始终是组小组件。
* 如果可能的选择数量有限，并且可以进行多个选择，请使用 CheckBoxGroup 小组件。如果只能从组中进行一个选择，请使用 RadioButtonGroup 小组件。若要显示所选内容列表，请使用 ListBox 小组件。
* Android: 如果将 Orientation 属性设置为水平，则不要在组中放置两个以上的项目。如果放置两个以上的项目，并且关联的文本很大，则其他项目可能不适合屏幕宽度，并且不可见。
* iPhone: 不能在开关视图中应用外观。
* SPA: 不支持焦点皮肤。

## Look 属性
略

## Skin Properties
对于 CheckBoxGroup 小组件，您可以将外观及其关联属性应用于以下状态：
* Normal 正常: 小组件的默认外观。
* Focus 重点: 当焦点位于小组件上时应用的皮肤。

## CheckBoxGroup 属性
* Master Data 主数据: 指定必须显示的一组值，以便用户从可用选项中进行选择。
* Selected Image 所选图像: 指定进行选择时要显示的图像。
* Unselected Image 未选择的图像: 指定清除所选内容时要显示的图像。
* Orientation 取向: 指定复选框的对齐方式是水平对齐还是垂直对齐。
* View Type 视图类型: 对于 iOS 平台，指定 CheckBoxGroup 的视图类型，即“开关”、“表”或“屏幕滚轮”。
* Group Cells 组单元格: 当视图类型为“表”时，指定是否应用“单元格组”样式。“组单元格”样式对复选框组中的项目进行分组。
* Tool Tip 工具提示: 对于 Windows 平板电脑平台，指定将鼠标指针悬停在小组件上时显示的消息。

## Actions 行动
* onSelection：选择项目时触发操作。
* onTouchStart：当用户触摸触摸表面时触发操作。此事件以异步方式发生。
* onTouchMove：当触摸在触摸表面上连续移动直到移动结束时，将触发该操作。此事件以异步方式发生。
* onTouchEnd：当用户触摸从触摸表面释放时触发操作。此事件以异步方式发生。