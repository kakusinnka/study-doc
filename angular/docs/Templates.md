# 概览
略

# 介绍
在 Angular 中，模板是用户界面 (UI) 片段的蓝图。模板是用 HTML 编写的，可以在模板中使用特殊语法来构建 Angular 的许多功能。

# 文本插值
插值是指将表达式嵌入到被标记的文本中。默认情况下，插值使用双花括号 {{ 和 }} 作为定界符。

# 模板语句
模板语句是可在 HTML 中用于响应用户事件的方法或属性。模板语句的语法是 (event)="statement"。  
模板语句解析器特别支持基本赋值 = 和带有分号 ; 的串联表达式。  
语句只能引用语句上下文中的内容，通常是组件实例。也可以引用模板自身的上下文属性。例如：
* 模板自己的 $event 对象用作参数。
* 模板输入变量。
* 模板输入变量。
* 模板语句的上下文可以是组件类实例或模板。因此，模板语句无法引用全局名称空间中的任何内容，比如 window 或 document。

模板自身上下文中的名称优先于组件上下文中的名称。

# 绑定
## 了解绑定
在 Angular 模板中，绑定会在从模板创建的一部分 UI（DOM 元素、指令或组件）与模型（模板所属的组件实例）之间创建实时连接。绑定的例子包括：文本插值，属性绑定，事件绑定，双向绑定。  
表达式上下文：通常，上下文就是组件实例。还可以引用模板上下文中的属性，比如模板输入变量或模板引用变量。模板表达式不能引用全局命名空间中的任何东西。  
Angular 会应用以下优先逻辑来确定上下文：1. 模板变量的名称。2. 指令上下文中的名称。3. 组件成员的名称。  
使用模板表达式时，请遵循以下最佳实践：使用短表达式，快速执行。

将数据值渲染为字符串时，可以使用任一种形式，只是插值形式更易读。但是，要将元素属性设置为非字符串数据值时，必须使用属性绑定。

## 属性(property)绑定
要绑定到元素的属性(property)，请将其括在方括号 [] 内，该括号会将属性标为目标属性。目标属性就是你要对其进行赋值的 DOM 属性。例如，以下代码中的目标属性是 img 元素的 src 属性。  
```
<img [src]="itemImageUrl">
```
方括号 [] 使 Angular 将等号的右侧看作动态表达式进行求值。如果不使用方括号，Angular 就会将右侧视为字符串字面量并将此属性设置为该静态值。  
绑定的几个使用场景：
* 将元素的属性设置为组件属性的值。
* 设置指令的属性。
* 设置自定义组件的模型属性。

## 属性(Attribute)绑定
Attribute 绑定语法类似于 Property 绑定，但不是直接在方括号之间放置元素的 Property，而是在 Attribute 名称前面加上前缀 attr，后跟一个点 .。然后，使用解析为字符串的表达式设置 Attribute 值。当表达式解析为 null 时，Angular 会完全删除该 Attribute。  

## 类和样式绑定
绑定到单个 CSS class：要创建单个类绑定，请使用前缀 class 后跟一个点和 CSS 类的名称，例如 [class.sale]="onSale"。onSale 为真值时添加类，在表达式为假值时（undefined 除外）删除类。  
绑定到多个 CSS 类：要绑定到多个类，请使用 [class] 来设置表达式 - 例如，[class]="classExpression"。表达式可以是用空格分隔的类名字符串，也可以是将类名作为键并将真或假表达式作为值的对象。对于对象格式，Angular 会在其关联的值为真时才添加类。  
绑定到单一样式：要创建对单个样式的绑定，请使用前缀 style 后跟一个点和 CSS style Attribute 的名称，例如 [style.width]="width"。 Angular 会将该 Attribute 设置为绑定表达式的值，这个值通常是一个字符串。（可选）你还可以添加单位扩展，例如 em 或 % ，它的值需要数字类型。
绑定到多个样式：要切换多个样式，请绑定到 [style] Attribute，例如 [style]="styleExpression" 。该表达式通常是样式的字符串列表，例如 "width: 100px; height: 100px;" 。你还可以将表达式格式化为对象，此对象以样式名作为键、以样式值作为值，例如 {width: '100px', height: '100px'}。

## 事件绑定
要绑定到事件，请使用 Angular 的事件绑定语法。此语法由等号左侧括号内的目标事件名和右侧引号内的模板语句组成。

## 双向绑定
双向绑定将属性绑定与事件绑定结合在一起：1. 属性绑定设置特定的元素属性。2. 事件绑定侦听元素更改事件。  
Angular 的双向绑定语法是方括号和圆括号的组合 [()]。[] 进行属性绑定，() 进行事件绑定。

# 管道
## 了解管道
使用管道来转换字符串、货币金额、日期和其他数据以进行显示。  
管道是在模板表达式中使用的简单函数，用于接受输入值并返回转换后的值。管道很有用，因为你可以在整个应用程序中使用它们，同时每个管道只声明一次。  
Angular 为典型的数据转换提供了内置的管道。  
管道操作符要比三目运算符（?:）的优先级高。

## 在模板中使用管道
要应用管道，请在模板表达式中使用管道运算符（|），如以下代码示例所示，以及管道名称，对于内置DatePipe来说是 date。  

## 使用参数和链式管道转换数据
可以用可选参数微调管道的输出。如果管道能接受多个参数，就用冒号分隔这些值。你可以使用任何有效的模板表达式作为参数，比如字符串字面量或组件的属性。  
可以对管道进行串联，以便一个管道的输出成为下一个管道的输入。

# 模板引用变量
模板变量可以帮助你在模板的另一部分使用这个部分的数据。  
模板变量可以引用这些东西：模板中的 DOM 元素，指令，元素，TemplateRef，Web 组件。  
在模板中，要使用井号 # 来声明一个模板变量。你可以在组件模板中的任何地方引用某个模板变量。  
Angular 根据你所声明的变量的位置给模板变量赋值：
* 如果在组件上声明变量，该变量就会引用该组件实例。
* 如果在标准的 HTML 标记上声明变量，该变量就会引用该元素。
* 如果你在 <ng-template> 元素上声明变量，该变量就会引用一个 TemplateRef 实例来代表此模板。
* 如果该变量在右侧指定了一个名字，比如 #var="ngModel" ，那么该变量就会引用所在元素上具有这个 exportAs 名字的指令或组件。

在大多数情况下，Angular 会把模板变量的值设置为它所在的元素。  
模板变量的作用域：
* 你可以在包含此模板变量的模板中的任何地方引用它。
* 而结构型指令充当了模板的边界。你不能在这些边界之外访问其中的模板变量。
* 内部模板可以访问外模板定义的模板变量。

# SVG 作为模板
当你用 SVG 作为模板时，可以像使用 HTML 模板一样使用指令和绑定。这意味着你可以动态生成交互式图形。  