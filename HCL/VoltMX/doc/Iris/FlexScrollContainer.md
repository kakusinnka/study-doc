# FlexScrollContainer
使用 FlexScrollContainer 小部件在窗体上创建一个可滚动的布局区域，该区域可以包含其他小部件。它可以包含任意数量的小部件。如果您不希望布局区域包含滚动条，请使用 FlexContainer 小部件。

## [Look 属性](./LookProperties.md)

## [Skin Properties 皮肤特性](.//UnderstandingSkinsAndThemes.md)

## FlexScrollContainer 属性
### Clip Bounds 剪辑边界
指定是否将子小组件裁剪到 FlexScrollContainer 的边界。

### Layout Type 布局类型
指定构件内容是水平、垂直还是双向流动。

### Enable Scrolling 启用滚动
指定是否启用滚动。

### Bounces 反弹
指定是否启用滚动跳回。

### Horizontal Bounce 水平反弹
指定是否在水平方向上启用滚动反弹。

### Vertical Bounce 垂直反弹
指定是否在水平方向上启用滚动反弹。

### Horizontal Scroll Indicator 水平滚动指示器
指定是否启用水平滚动指示器。

### Vertical Scroll Indicator 垂直滚动指示器
指定是否启用垂直滚动指示器。

### Paging 分页
指定是否为滚动启用分页。

### Scroll Direction 滚动方向
指定滚动方向，水平、垂直或水平和垂直。

### Content Offset X 内容偏移量 X
指定可滚动区域左上角的 X 坐标。设置内容偏移值后，即使禁用滚动，FlexScrollContainer 也会滚动。该值不反映实际计算的偏移量。

### Content Offset Y 内容偏移量 Y
指定可滚动区域左上角的 Y 坐标。设置内容偏移值后，即使禁用滚动，FlexScrollContainer 也会滚动。该值不反映实际计算的偏移量。

### Content Size Width 内容大小宽度
指定 FlexScrollContainer 宽度以容纳放置在其中的所有小组件。该值不反映实际计算的内容大小。

### Content Size Height 内容大小高度
指定 FlexScrollContainer 高度以容纳放置在其中的所有小组件。该值不反映实际计算的内容大小。

### Snap to Grid 对齐到网格
指定构件是与网格中最近的线的交点对齐，还是与其他构件对齐。

### Snap Grid Size 捕捉网格大小
指定网格大小。仅当启用了“对齐到网格”时，此选项才可用。

### Default Unit 默认单位
指定在传递给布局属性时用于解释不带限定符的数字的默认单位。

### Zoom Scale 缩放比例
指定应用于 FlexScrollContainer 内容的比例因子。

### Min Zoom Scale 最小缩放比例
指定可应用于 FlexScrollContainer 的最小缩放比例因子。

### Max Zoom Scale 最大缩放比例
指定可应用于 FlexScrollContainer 的最大缩放比例因子。

### Bounces Zoom 反弹缩放
指定当缩放超过最大或最小限制时，滚动视图是否对内容缩放进行动画处理。如果“反弹缩放”设置为“打开”，并且缩放超出了缩放的最小或最大限制，则滚动视图会暂时对刚好超过限制的内容缩放进行动画处理，然后再返回到限制。如果“Bounces Zoom”设置为“关闭”，则缩放在达到缩放限制时会立即停止。

## Actions 行动
操作定义事件发生时发生的情况。在 FlexScrollContainer 小组件上，您可以在发生以下事件时运行操作：
* onScrollStart：当用户开始滚动内容时，将触发该操作。此事件以异步方式发生。
* onScrollTouchReleased：当用户的触摸从触摸表面释放时，将触发该操作。此事件以异步方式发生。
* onScrolling：滚动过程中触发操作。此事件以异步方式发生。
* onDecelerationStarted: 当用户停止滚动但内容在实际停止之前仍在移动时，会触发此操作。此事件异步发生。
* onScrollEnd：滚动结束时触发操作。此事件以异步方式发生。
* onTouchStart：当用户触摸触摸表面时触发操作。此事件以异步方式发生。
* onTouchMove：当触摸在触摸表面上连续移动直到移动结束时，将触发该操作。此事件以异步方式发生。
* onTouchEnd：当用户的触摸从触摸表面释放时触发操作。此事件以异步方式发生。
* widgetToZoom: 平台调用事件回调来返回要缩放的源子控件之一。返回的源本身使整个滚动容器可缩放。如果返回空值，则容器不会缩放。此事件异步发生。
* onZoomStart：当 FlexScrollContainer 即将缩放时触发该操作。此事件以异步方式发生。
* onZooming：当 FlexScrollContainer 缩放时触发该操作。此事件以异步方式发生。
* onZoomEnd：缩放结束时触发操作。此事件以异步方式发生。

