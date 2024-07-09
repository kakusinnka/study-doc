# Switch 开关
使用“切换”小组件让用户在两个互斥的选项或状态之间进行选择，类似于 iPhone 上的“切换”控件。“开关”小组件显示当前生效的值。滑动控件以选择或显示其他值。

## 重要考虑因素
以下是 Switch 小组件的重要注意事项：
* 使用一对可预测的值，这样用户就不必滑动开关即可知道另一个值。
* 请考虑使用“切换”小组件来更改视图中其他用户界面元素的状态。

## Look 看
略

## Skin 皮肤
* Normal 正常：小组件的默认外观。
* Focus 重点：当焦点集中在小组件上时应用的皮肤。
* Thumb Color 拇指颜色：开关滑块按钮的颜色。当您为 iPhone Native 分叉皮肤时，以及当您为 Android Native 分叉整个窗体时，此属性在 BackGround 下可用。
* Tint Color 色调颜色：仅当您为 iPhone Native 分叉皮肤时，此属性在 BackGround 下可用。

## Switch Properties 开关属性
### State
允许您切换开关颜色。

### Left Text 左文字
指定要在开关左侧显示的文本。

### Right Text 右文本
指定要在开关右侧显示的文本。

## Actions 行动
* onSlide：当默认所选值发生更改时，将触发该操作。
* onTouchStart：当用户触摸触摸表面时触发操作。此事件以异步方式发生。
* onTouchMove：当触摸在触摸表面上连续移动直到移动结束时，将触发该操作。此事件以异步方式发生。
* onTouchEnd：当用户触摸从触摸表面释放时触发操作。此事件以异步方式发生。