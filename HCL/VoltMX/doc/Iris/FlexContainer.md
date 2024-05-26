# FlexContainer
使用 FlexContainer 小组件在可以包含其他小组件的窗体上创建布局区域。如果希望布局区域包含滚动条，请使用 FlexScrollContainer 小组件。

## [Look 属性](./LookProperties.md)
外观属性定义小组件的外观。以下是您可以设置的主要属性：
* 小组件是否可见。
* 呈现小组件的平台。
* 小组件如何与其父小组件和相邻小组件对齐。
* 如果小组件显示内容，则显示内容的位置。

### FlexContainer 小部件的自动增长
通过将“外观”选项卡上的“高度”属性设置为“首选”，可以指定 FlexContainer 小组件根据其子小组件的高度动态调整其高度。然后，当任何子小部件的高度发生变化时，FlexContainer 的高度会进行调整。

局限性：
* 如果未提供子小组件的顶部或底部值，则在确定 FlexContainer 的高度时将使用零值。
* 如果小组件的高度随着小组件的外观状态更改（例如，从正常状态更改为焦点）而变化，则 FlexContainer 的高度将不会动态增长。
* 如果微件的顶部值为负数，则在“自由形式”的情况下，该微件将被裁剪，并在“垂直流”中的上一个微件上重叠。
* 当 FlexContainer 放置在 HBox 或 VBox 中时，它不会动态增长。
* 如果禁用了子 FlexContainer 的剪辑边界，则超出边界的子 FlexContainer 的子项不会影响父 FlexContainer 的高度。仅使用父 FlexContainer 的直接子级的高度来确定其高度。
* 仅当 Segment2 视图类型为表视图时，使用 FlexContainer 创建的 Segment 模板才会动态增长。
* FlexContainer 动态增长在 Tab Widget 上不受支持。
* 在 Windows 平台中，如果将 Segment 2 小组件放置在 FlexContainer 中，则不支持 Segment2 Auto Grow 属性。

## [皮肤特性](./UnderstandingSkinsAndThemes.md)
外观属性定义小组件的外观，包括背景颜色、边框和阴影。如果构件包含文本，您还可以指定文本字体。

对于 FlexContainer 小组件，您可以将外观及其关联属性应用于以下状态：
* Normal: 小组件的默认外观。
* Focus: 当小组件具有焦点时应用的皮肤。
* Blocked UI: 应用于阻止接口的外观，直到正在进行的操作（例如，服务调用）完成。> 注意：阻止的 UI 仅适用于 SPA 平台。

### Clip Bounds 剪辑边界
指定是否在子构件超出边界时对其进行裁剪。

### Layout Type 布局类型
指定 FlexContainer 中小组件的排列是水平、垂直还是双向流动。

### Child Widget Align 子小部件对齐
指定 FlexContainer 的子小组件中小组件的排列是水平、垂直还是双向流动。

### Snap to Grid 对齐到网格
指定构件是与网格中最近的线的交点对齐，还是与其他构件对齐。

### Snap Grid Size 捕捉网格大小
指定网格大小。仅当启用了“对齐到网格”时，此选项才可用。

### Default Unit 默认单位
指定在传递给布局属性时用于解释不带限定符的数字的默认单位。

* dp：指定与设备无关的像素的值。
* px：以设备硬件像素为单位指定值。
* %：以相对于父维度的百分比表示指定值。

### Swipe Config 滑动配置
您可以配置 Segment 小部件的滑动功能。通过轻扫配置设置，用户可以在向左或向右轻扫行时关闭行或显示某些操作。

## Actions
操作定义事件发生时发生的情况。在 FlexContainer 小组件上，您可以在发生以下事件时运行操作：
* onTouchStart：当用户触摸触摸表面时触发操作。此事件以异步方式发生。
* onTouchMove：当触摸在触摸表面上连续移动直到移动结束时，将触发该操作。此事件以异步方式发生。
* onTouchEnd：当用户触摸从触摸表面释放时触发操作。此事件以异步方式发生。
* onClick：当用户单击小组件时触发操作。
* onSwipeLeft：当您向左滑动“区段”小组件的一行时，将触发此操作。仅当启用启用轻扫和启用左轻扫选项，并且区段模板的“类型”设置为“轻扫以关闭”时，此操作才可用。
* onSwipeRight：当您向右滑动 Segment 小组件的一行时，将触发该操作。仅当启用“轻扫”和“启用向右轻扫”选项，并且“区段”模板的“类型”设置为“轻扫以关闭”时，此操作才可用。