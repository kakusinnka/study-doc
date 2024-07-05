# Map 地图
使用“地图”微件在地图上显示位置。iPhone（3.0 以上）和 Android 等平台提供了原生地图小部件，可以作为应用程序的一部分显示。

## Look Properties Look 属性
略

## Map Properties 地图属性
### Callout Template 标注模板
指定地图标注的模板（例如，图钉），用于指示地图上的特定位置。该模板可以包括 Label、Link、RichText、Button 和 Image 小部件。

### Pin Image 图钉图像
指定用于指示地图上位置的图钉图像。默认映像由系统提供。

### Mode 模式
指定地图查看模式。

### Source 源
指定映射源。

### Zoom Level 缩放级别
指定当前地图视图的缩放级别。

### Full Screen Widget 全屏小部件
指定“地图”微件是否占据全屏。

### Callout Width 标注宽度
指定地图上标注的宽度。您可以指定一个介于 1 和 100 之间的值，该值表示相对于“地图”微件宽度的百分比。

### Height 高度
将地图的高度指定为相对于 Height Reference 属性值的百分比。

### Height Reference 高度参考
指定地图高度的计算方式

### Show Current Location 显示当前位置
指定是否以及如何指示地图上的当前位置

### Zoom Control 变焦控制
指定是否在地图上显示缩放控件。

## Actions 行动
* onClick：单击地图时，平台会调用该操作。
* onPinClick：当用户点击地图图钉，将选定的 locationdata 传递给回调时，会触发该操作。
* onSelection：当用户单击地图标注时，将触发该操作。
* onMapLoaded：地图渲染完成后，平台将调用该操作。
* onBoundsChanged：当地图内容发生变化时，平台会调用该操作