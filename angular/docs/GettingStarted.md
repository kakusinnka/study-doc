# 什么是 Angular
Angular 是一个基于 TypeScript 构建的开发平台。作为一个平台，Angular 包括：
* 用于构建可扩展 Web 应用程序的基于组件的框架。
* 一系列集成良好的库，涵盖多种功能，包括路由、表单管理、客户端-服务器通信等。
* 一套开发人员工具，可帮助您开发、构建、测试和更新代码。

## Angular 应用程序：要点
本节解释 Angular 背后的核心思想。 了解这些想法可以帮助您更有效地设计和构建应用程序。

### 组件 (Components)
组件是组成应用程序的构建块。组件包含带有 @Component() 装饰器的 TypeScript 类、HTML 模板和样式。  
@Component() 装饰器指定以下 Angular 特定信息：
* 定义如何在模板中使用组件的 CSS 选择器。模板中与此选择器匹配的 HTML 元素将成为该组件的实例。
* 指示 Angular 如何渲染组件的 HTML 模板
* 一组可选的 CSS 样式，用于定义模板 HTML 元素的外观

### 模板 (Templates)
每个组件都有一个 HTML 模板，用于声明该组件的呈现方式。您可以内联或通过文件路径定义此模板。  
Angular 添加了扩展 HTML 的语法元素，以便您可以从组件插入动态值。当组件的状态发生变化时，Angular 会自动更新渲染的 DOM。  
```
<p>{{ message }}</p>
```
Angular 还支持属性绑定，以帮助您设置 HTML 元素的属性和特性的值，并将值传递到应用程序的表示逻辑。  
```
<p
  [id]="sayHelloId"
  [style.color]="fontColor">
  You can set my color in the component!
</p>
```
声明事件侦听器来侦听并响应用户操作，例如击键、鼠标移动、单击和触摸。您可以通过在括号中指定事件名称来声明事件侦听器：
```
<button
  type="button"
  [disabled]="!canClick"
  (click)="sayMessage()">
  Trigger alert message
</button>
```
使用指令向模板添加功能。 Angular 中最流行的指令是 *ngIf 和 *ngFor 。使用指令执行各种任务，例如动态修改 DOM 结构。并创建您自己的自定义指令以创造出色的用户体验。  
Angular 的声明性模板可让您将应用程序的逻辑与其表示清晰地分开。模板基于标准 HTML，以便于构建、维护和更新。  

### 依赖注入 (Dependency injection)
依赖注入让你可以声明 TypeScript 类的依赖关系，而无需关心它们的实例化。相反，Angular 会为您处理实例化。这种设计模式可以让您编写更可测试、更灵活的代码。  

## Angular CLI
Angular CLI 是开发 Angular 应用程序最快、最直接且推荐的方式。 Angular CLI 使某些任务变得毫无麻烦。  

## 第一方库 (First-party libraries)
略

# 尝试 Angular
## 入门
## 添加导航
## 管理数据
## 使用表单进行用户输入
## 部署应用程序

# 设置