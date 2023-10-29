# 基本概念简介
![Angular 基本部分之间的关系](https://angular.io/generated/images/guide/architecture/overview2.png)
Angular 是一个使用 HTML 和 TypeScript 构建单页客户端应用程序的平台和框架。Angular 是用 TypeScript 编写的。它以一组导入到应用程序中的 TypeScript 库的形式实现核心和可选功能。

## 模块
将代码组织到不同的功能模块中有助于管理复杂应用程序的开发，以及设计可重用性。此外，此技术还允许您利用延迟加载（即按需加载模块）来最大程度地减少启动时需要加载的代码量。

## 组件
组件定义了一个包含应用程序数据和逻辑的类，并与一个 HTML 模板相关联，该模板定义要在目标环境中显示的视图。

### 模板、指令和数据绑定
模板将 HTML 与 Angular 标记相结合，可以在显示 HTML 元素之前对其进行修改。模板指令提供程序逻辑，绑定标记将应用程序数据与 DOM 连接起来。有两种类型的数据绑定：
* 事件绑定：允许应用程序通过更新应用程序数据来响应目标环境中的用户输入。
* 属性绑定：允许您将从应用程序数据计算的值插值到 HTML 中。

在显示视图之前，Angular 会根据程序数据和逻辑评估指令并解析模板中的绑定语法，以修改 HTML 元素和 DOM。Angular 支持双向数据绑定，这意味着 DOM 中的更改（例如用户选择）也会反映在程序数据中。

模板可以使用管道通过转换显示值来改善用户体验。

## 服务和依赖关系注入
对于未与特定视图关联的数据或逻辑，以及要跨组件共享的数据或逻辑，请创建一个服务类。服务类定义紧跟 @Injectable() 在装饰器的前面。修饰器提供元数据，允许将其他提供程序作为依赖项注入到类中。

### 路由
Angular Router NgModule 提供了一项服务，可让您在不同的应用程序状态和查看应用程序中的层次结构之间定义导航路径。


# 模块简介
Angular 应用程序是模块化的，Angular 有自己的模块化系统，称为 NgModules。NgModules 是专用于应用程序域、工作流或一组密切相关的功能的内聚代码块的容器。它们可以包含组件、服务提供程序和其他代码文件，其范围由包含的 NgModule 定义。它们可以导入从其他 NgModule 导出的功能，并导出选定的功能以供其他 NgModule 使用。

这是一个简单的根 NgModule 定义。  
```
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

@NgModule({
  // 此 NgModule 中声明的组件模板需要其导出类的其他模块。
  imports:      [ BrowserModule ],
  // 此 NgModule 为全局服务集合做出贡献的服务创建者;它们可以在应用程序的所有部分访问。（还可以在组件级别指定提供程序。）
  providers:    [ Logger ],
  // 声明属于此 NgModule 的组件、指令和管道。
  declarations: [ AppComponent ],
  // 在其他 NgModule 的组件模板中应该可见和可用的声明子集。
  exports:      [ AppComponent ],
  // 主应用程序视图，称为根组件，它承载所有其他应用程序视图。只有根 NgModule 才能设置该 bootstrap 属性。
  bootstrap:    [ AppComponent ]
})
export class AppModule { }
```


# 组件简介
组件控制称为视图的屏幕补丁。它由一个TypeScript类，一个HTML模板和一个CSS样式表组成。TypeScript 类定义 HTML 模板和呈现的 DOM 结构的交互，而样式表描述其外观。

## 组件元数据
下面是 HeroListComponent 的基本组件元数据示例。  
```
@Component({
  // 一个 CSS 选择器，它告诉 Angular 在模板 HTML 中找到相应标签的任何地方创建并插入此组件的实例。
  selector:    'app-hero-list',
  // 此组件的 HTML 模板的模块相对地址。或者，可以提供内联的 HTML 模板作为 template 属性的值。此模板定义组件的主机视图。
  templateUrl: './hero-list.component.html',
  // 组件所需服务的提供程序数组。
  providers:  [ HeroService ]
})
export class HeroListComponent implements OnInit {
  /* . . . */
}
```

## 模板和视图
### 模板语法
模板看起来像常规 HTML，只是它还包含 Angular 模板语法，它会根据应用程序的逻辑以及应用程序和 DOM 数据的状态来更改 HTML。模板可以使用数据绑定来协调应用程序和 DOM 数据，使用管道在显示数据之前转换数据，以及使用指令将应用程序逻辑应用于显示的内容。  
* [数据绑定](https://angular.io/generated/images/guide/architecture/databinding.png)
* 管道
* 指令：结构指令，属性指令


# 服务和依赖注入简介
理想情况下，组件的工作是仅启用用户体验。组件应提供数据绑定的属性和方法，以便在视图和应用程序逻辑之间进行调解。视图是模板呈现的内容，应用程序逻辑是包含模型概念的内容。

组件应将服务用于不涉及视图或应用程序逻辑的任务。服务适用于从服务器获取数据、验证用户输入或直接登录到控制台等任务。通过在可注入服务类中定义此类处理任务，可以使这些任务可用于任何组件。您还可以通过注入相同类型服务的不同提供程序（视不同情况而定）使应用程序更具适应性。

## 依赖注入 
依赖注入 （DI） 是 Angular 框架的一部分，它为组件提供了对服务和其他资源的访问权限。Angular 使您能够将服务注入组件，以授予该组件访问服务的权限。

### 提供服务


# 后续步骤
## 应用程序体系结构
## 响应式编程
## 客户端-服务器交互
## 支持开发周期
## 文件结构、配置和依赖关系
## 扩展 Angular


# 绑定语法
数据绑定会根据应用程序的状态自动使页面保持最新。使用数据绑定可以指定图像源、按钮状态或特定用户的数据等内容。

## 数据绑定和 HTML
请注意，绑定是按钮 disabled 的 DOM 元素的属性(properties)，而不是 HTML 的属性(attributes)。数据绑定使用 DOM 元素、组件和指令的属性，而不是 HTML 属性(attributes)。

### HTML attributes and DOM properties
在 Angular 中，HTML 属性的唯一作用是初始化元素和指令状态。  
编写数据绑定时，您只处理目标对象的 DOM 属性和事件。

## 数据绑定的类型
Angular 根据数据流的方向提供三类数据绑定：
* 从源到视图[]
* 从视图到源()
* 在从源到视图的双向[()]

## 绑定类型和目标
* Property：
* Event
* Two-way
* Attribute
* class property
* style property


# 事件绑定的工作原理
在事件绑定中，Angular 会为目标事件配置事件处理函数。你还可以将事件绑定用于自定义事件。  
当组件或指令引发事件时，处理程序就会执行模板语句。模板语句会执行一个动作来响应这个事件。  
目标事件决定了 $event 对象的形态。如果目标事件是来自原生 DOM 元素的，那么 $event 是一个DOM 事件对象，它具有 target 和 target.value 等属性。  
如果该事件属于某个指令或组件，那么 $event 就具有指令或组件中生成的形态。


# 了解模板变量
模板变量可帮助您在模板的另一部分中使用模板一部分的数据。使用模板变量来执行任务，例如响应用户输入或微调应用程序的表单。  
模板变量可以引用以下内容：
* 模板中的 DOM 元素
* 指令或组件
* 来自 ng-template 的 TemplateRef
* Web 组件

## 语法
在模板中，使用 *#* 来声明模板变量。

## Angular 如何为模板变量赋值
Angular 根据你声明变量的位置为模板变量分配一个值：
* 如果在组件上声明变量，则该变量将引用组件实例。
* 如果在标准 HTML 标记上声明变量，则该变量将引用该元素。
* 如果在 <ng-template> 元素上声明变量，则该变量将引用表示模板的 TemplateRef 实例。

## 指定名称的变量
如果变量在右侧指定了名称，例如 #var="ngModel" ，则该变量引用具有匹配 exportAs 名称的元素上的指令或组件。

### NgForm 与模板变量一起使用
```
<form #itemForm="ngForm" (ngSubmit)="onSubmit(itemForm)">
  <label for="name">Name</label>
  <input type="text" id="name" class="form-control" name="name" ngModel required />
  <button type="submit">Submit</button>
</form>

<div [hidden]="!itemForm.form.valid">
  <p>{{ submitMessage }}</p>
</div>
```

## 模板变量作用域
就像 JavaScript 或 TypeScript 代码中的变量一样，模板变量的范围限定为声明它们的模板。

同样，结构指令（如 *ngIf and 或 <ng-template> 声明）会创建一个新的嵌套模板作用域，就像 JavaScript 的控制流语句（如 if and *ngFor ） for 创建新的词法作用域一样。您无法从其中一个结构指令的边界外部访问模板变量。

### 在嵌套模板中访问

## 模板输入变量
```
<ul>
  <ng-template ngFor let-hero let-i="index" [ngForOf]="heroes">
    <li>Hero number {{i}}: {{hero.name}}
  </ng-template>
</ul>
```