# 应用程序菜单小部件 （ 标签栏 ）
应用程序菜单（应用程序菜单）是显示在应用程序底部的栏，其中包含适用于应用程序的功能的图标，而不是应用于特定应用程序屏幕或窗口的功能。

## UI Appearance UI 外观
* Focus Skin 聚焦皮肤：指定焦点集中在应用程序菜单上的外观。
* Skin 皮肤：指定应用程序菜单的外观。

## Data Management 数据管理
* addAppMenuItemAt：在给定索引处添加应用程序菜单项。
* createAppMenu 创建AppMenu：允许您通过代码动态创建应用程序菜单。
* getAppMenuBadgeValue：使您能够读取附加到给定 Appmenu 项的锁屏提醒值（如果有）。
* getCurrentAppMenu：返回通过 setCurrentAppMenu 设置的当前应用菜单的唯一标识符。
* removeAppMenuItemAt：删除指定的应用程序菜单项。
* setAppMenuBadgeValue：允许您在菜单项的右上角为给定的应用程序菜单项设置锁屏提醒值。
* setAppMenuFocusByID：采用 ID（使用 createAppMenu 设置）而不是 index，并将焦点设置在当前应用菜单的菜单项上。
* setCurrentAppMenu：使用表示应用程序菜单的唯一标识符，并将其设置为当前应用程序菜单。

## Internationalization 国际化
i18n Key i18n 键：指定用于国际化的 i18n 密钥。

## 3D Touch 3D 触控
* registerForPeekandPop 注册 ForPeekandPop：注册小组件以启用 3D Touch 速览和弹出手势。
* setOnPeek：设置并覆盖小组件的现有 onPeekCallback。
* setOnPop：覆盖小组件的现有 onPopCallback。
* unregisterForPeekandPop 取消注册ForPeekandPop：从 3D Touch 速览和弹出手势中取消注册小组件。

## User Input Handling 用户输入处理
* addGestureRecognizer：允许您为指定小组件的指定手势设置手势识别器。
* removeGestureRecognizer：允许您删除指定小组件的指定手势识别器。
* setGestureRecognizer：允许您为指定小组件的指定手势设置手势识别器。

## Animations 动画
* Animate 动画：将动画应用于小组件。

## Miscellaneous 杂项
* getBadge 获取徽章：用于读取附加到指定小组件的锁屏提醒值（如果有）。
* 用于将锁屏提醒值设置为小组件右上角的给定小组件。
* Appbar Button Style Appbar 按钮样式：指定应用程序栏的按钮样式。
* Event 事件：指定“应用程序菜单”项的事件。
* Icon 图标：指定要为“应用程序菜单”项显示的图像。
* Position 位置：指定应用程序栏按钮的位置。
* Render 呈现：指定生成代码时是否必须将小组件代码包含在平台中。
* Title 标题：指定应用程序菜单的常规文本或描述性文本。

## Enabling RTL 启用 RTL
略

## 所有小部件通用的配置
* convertPointFromWidget：允许您将坐标系从微件转换为点（接收方的坐标系）。
* convertPointToWidget：允许您将坐标系从点（接收方的坐标系）转换为微件。
* removeFromParent 删除FromParent：允许您从父小组件中删除子小组件。
* setEnabled set启用：指定必须启用或禁用的小组件。
* setFocus setFocus（集聚焦）：指定必须关注的小组件。
* setVisibility set可见性：使用此方法可设置小组件的可见性。
* ID：应用程序菜单的唯一标识符，由字母数字字符组成。

# AppMenu Widget 基础知识
## Android 特定行为
* 如果添加的 App Menu 项超过 6 个，则第 5 个 App Menu 项之外的菜单项将分组到“菜单项更多”（由 Android 平台自动添加）下，如果选择“更多”，则其余菜单项将显示在列表中，不显示任何图标（即使图标是通过代码设置的）。这是 Android 平台支持中的一个限制。
* 不能为“应用菜单”指定外观。

## iOS 特定行为
* 在 iOS 7 和 iOS 7.1 中，AppMenu 仅支持单色。如果未指定颜色，则默认情况下，原生颜色（透明）应用于 iOS 7，青色应用于 iOS7.1。
* 如果添加的 App 菜单项超过 5 个，则第四个 App Menu 项之外的菜单项将分组到菜单项“更多”（由 iOS 平台自动添加）下，如果选择“更多”，则菜单项的其余部分将显示在列表中，并为它们设置了图标。
* 当从具有 AppMenu 的窗体到没有 AppMenu 的窗体的过渡流时，不支持过渡动画。