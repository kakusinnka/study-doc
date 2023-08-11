# Overview 概述
组件是 Angular 应用程序的主要构建块。每个组件包括：
* 声明页面上呈现内容的 HTML 模板
* 定义行为的 TypeScript 类
* 定义如何在模板中使用组件的 CSS 选择器
* （可选）应用于模板的 CSS 样式


## 先决条件
略

## 创建组件
创建组件的最佳方法是使用 Angular CLI。您也可以手动创建组件。  
### 使用 Angular CLI 创建组件
要使用 Angular CLI 创建组件：要使用 Angular CLI 创建组件：运行 ng generate component *component-name* 命令，其中 *component-name* 是新组件的名称。
### 手动创建组件
略

## 指定组件的 CSS 选择器
略

## 定义组件的模板
略

## 声明组件的样式
略

# Component lifecycle 组件生命周期
Angular 组件的生命周期是指在组件从创建到销毁的整个过程中，Angular 框架提供的一系列钩子函数，允许你在不同的时机插入自定义代码。这些钩子函数可以用于执行各种任务，如初始化、数据加载、DOM 操作、清理等。  
## 先决条件
略

## 响应生命周期事件
### 生命周期事件序列
在您的应用程序通过调用其构造函数来实例化组件或指令后，Angular 会调用您在该实例生命周期中的适当点实现的钩子方法。  
### ngOnChanges
ngOnChanges() 是 Angular 组件生命周期中的一个钩子函数，子组件用于监测每个输入属性（@Input）（也就是父组件的属性）的变化。它会在子组件的输入属性发生变化时被触发，允许你在属性变化时在子组件中执行相应的操作。  

### ngOnInit
ngOnInit() 是 Angular 组件生命周期中的一个钩子函数，它在组件初始化完成后被调用。在该钩子函数中，你可以执行初始化数据、订阅数据、进行一次性的 DOM 操作等。  

### ngDoCheck
Angular 的变更检测机制关注于组件属性、输入属性、模板表达式、Observable 和异步操作等与数据相关的对象，以及通过 ngDoCheck() 钩子函数实现的自定义检测逻辑。这些对象共同构成了 Angular 变更检测的范围。  
ngDoCheck() 是 Angular 组件生命周期中的一个钩子函数，它在每次变更检测周期中被调用。它允许你监测和响应组件的数据变化，以及手动触发变更检测。在第一次运行 ngOnInit() 之后也会立即调用。ngDoCheck() 钩子函数通常用于执行一些高级的、自定义的变更检测逻辑。  

### ngAfterContentInit
内容投影（Content Projection），也称为内容插槽（Content Slots）或内容分发（Content Distribution），是 Angular 中一种强大的特性，允许你在一个组件中嵌入外部的内容，以及在父组件中定义子组件的布局结构。内容投影通过 *ng-content* 标签来实现，它允许父组件将内容传递到子组件中，从而在子组件的特定位置显示这些内容。  
ngAfterContentInit() 是 Angular 组件生命周期中的一个钩子函数，它在组件的内容投影（Content Projection）初始化完成后被调用。内容投影是一种将父组件的内容嵌入到子组件中的技术，通常使用 *ng-content* 标签实现。

### ngAfterContentChecked
ngAfterContentChecked() 是 Angular 组件生命周期中的一个钩子函数，用于在内容投影的变更检测后执行操作。通过合理地使用 ngAfterContentChecked()，你可以在内容投影变更检测后执行相应的逻辑，以满足组件的需求。  

### ngAfterViewInit
ngAfterViewInit() 是 Angular 组件生命周期中的一个钩子函数，它在组件的视图初始化完成后被调用。在这个阶段，组件的视图已经初始化，但还没有添加到 DOM 中。这个钩子函数通常用于执行一次性的初始化操作，比如与视图相关的 DOM 操作、订阅事件等。

### ngAfterViewChecked
ngAfterViewChecked() 是 Angular 组件生命周期中的一个钩子函数，它在每次视图变更检测周期中，检测和更新视图后被调用。视图变更检测是 Angular 中用于检测组件数据的变化并更新视图的机制。  

### ngOnDestroy
ngOnDestroy() 是 Angular 组件生命周期中的一个钩子函数，它在组件即将被销毁时被调用。这个钩子函数允许你在组件被销毁前执行一些清理操作，比如取消订阅、释放资源等。


# View encapsulation 查看封装
# Component interaction 组件交互
# Component styles 组件样式
# Sharing data between child and parent directives and components
# 在子指令和父指令和组件之间共享数据
# Content projection 内容投影
# Dynamic components 动态组件
# Angular elements 角元素