# TabPane
使用 TabPane 小组件组织多个选项卡。每个选项卡都包含窗体上的小部件集合。用户一次查看一个选项卡。

## 重要考虑因素
以下是 TabPane 小组件的重要注意事项：
* 您只能使用向下键在 TabPane 中导航。
* 如果按向下键，焦点将移至 TabPane 中的下一个小组件。
* 如果在 TabPane 中的最后一个小组件上按向下键，您将被带到 TabPane 中最顶部的小组件。
* 如果按向右或向左箭头键，则移动到下一个或上一个选项卡。
* 支持 Tab 键循环（也就是说，如果您在最后一个选项卡上并按向右箭头，则移动到第一个选项卡）。
* 在具有导航键的设备上，以下内容适用：
  * 每个选项卡都有一个上下文菜单。当选项卡具有焦点时，上下文菜单将显示在菜单选项中。
  * 选项卡中的小组件焦点已保存。例如，如果 Tab2 的 Widget2 具有焦点，并且您导航到 Tab1，然后返回到 Tab2，则 Widget2 仍然具有焦点。

## Look 属性
对于 TabPane 小组件，您可以将外观及其关联属性应用于以下状态：
* Active：当 TabPane 处于活动状态时应用的外观。
* Active Focus：当 TabPane 处于活动状态并具有焦点时应用的外观。
* Inactive：应用于非活动选项卡的皮肤。
* Page：页面指示器的外观。仅当“视图类型”设置为“页面”，并且为“聚焦页面”和“非聚焦页面”图标指定了图像时，外观才适用。

## TabPane 属性
### Active Tabs 活动选项卡
指定 TabPane 中的选项卡是处于活动状态还是处于非活动状态。

### Full Screen Widget 全屏小部件
对于 VBox 窗体上的 TabPane，指定 TabPane 是否占用整个窗体。

### View Type 视图类型
指定每个平台的 TabPane 视图类型。若要指定视图类型，请单击“编辑”按钮打开“视图类型”对话框，选择一个平台，然后选择视图类型。
* Tab
* Collapsible 折叠式
* Page（仅限 iPhone 和 Android）
* Panorama（仅限 Windows）

### Height 高度
将 TabPane 的高度指定为“高度引用”属性的百分比。

### Height Reference 高度参考
指定“高度百分比”的计算方式。

* 表单参考：高度百分比根据表单的高度计算，不包括页眉和页脚。如果 TabPane 放置在弹出窗口或模板中，则此选项不适用。
* 父宽度：如果 TabPane 放置在弹出窗口或模板中，则根据父容器的宽度计算宽度。

### Progress Indicator 进度指示器
指定是否显示进度指示器。

### 进度指示器颜色
指定进度指示器的颜色，灰色或白色。

### Tab Header Height 选项卡标题高度
指定制表符标题的高度。

## Actions 行动
操作定义事件发生时发生的情况。在 Tab 小组件上，您可以在发生以下事件时运行操作：

### onTabClick
单击选项卡时触发操作。仅当“视图类型”设置为“可折叠视图”时，此操作才可用，并在展开或折叠选项卡时触发。

### onTouchStart
当用户触摸触摸表面时触发操作。此事件以异步方式发生。

### onTouchMove
当触摸在触摸表面上连续移动直到移动结束时，将触发该操作。此事件以异步方式发生。

### onTouchEnd
当用户触摸从触摸表面释放时触发操作。此事件以异步方式发生。
