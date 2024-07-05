# PickerView
使用 PickerView 小组件使用户能够从多组值中选择单个值组合。用户使用选择指示器轮换每组值。例如，用户可以从月份、月份中的几天和年份列表中选择单个日期。

## Look Properties Look 属性
略

## Skin Properties 皮肤特性
略

## PickerView 属性
### Master Data 主数据
指定 PickerView 小组件中显示的值。

### View Type 视图类型
对于 Android 平台，指定选取器视图类型。扁平：拣选器外观扁平。滚轮：拾取器显示为滚轮。

### Enable Cache 启用缓存
对于 Windows 8 平台，指定是否相对于 PickerView 小组件缓存数据。

## Actions 行动
* onSelection：当组件选择更改时触发操作。
* onTouchStart：当用户触摸触摸表面时触发操作。此事件以异步方式发生。
* onTouchMove：当触摸在触摸表面上连续移动直到移动结束时，将触发该操作。此事件以异步方式发生。
* onTouchEnd：当用户触摸从触摸表面释放时触发操作。此事件以异步方式发生。