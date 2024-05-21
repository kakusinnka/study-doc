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