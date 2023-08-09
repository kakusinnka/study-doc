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
### 开始使用 Angular
本教程将引导您构建一个包含目录、购物车和结账表单的电子商务网站，从而向您介绍 Angular 的基本知识。

### 先决条件
略

### 浏览示例应用程序
您可以使用组件构建 Angular 应用程序。组件定义 UI 中的责任区域，使您可以重用 UI 功能集。  
一个组件由三部分组成：
* 一个组件类：处理数据和功能。
* 一个 HTML 模板：确定用户界面。
* 组件特定样式：定义外观和感觉。

### 创建示例项目
略

### 创建产品列表
略

### 将数据传递给子组件
子组件使用 @Input() 装饰器定义属性。
```
import { Component, Input } from '@angular/core';
import { Product } from '../products';

export class ProductAlertsComponent {

  @Input() product: Product | undefined;

}
```

使用属性绑定将数据传递给子组件。
```
<app-product-alerts
  [product]="product">
</app-product-alerts>
```

### 将数据传递给父组件
子组件:
```
import { Component, Input, Output, EventEmitter } from '@angular/core';
import { Product } from '../products';

export class ProductAlertsComponent {
  @Output() notify = new EventEmitter();
}
```
```
<p *ngIf="product && product.price > 700">
  <button type="button" (click)="notify.emit()">Notify Me</button>
</p>
```

父组件:
```
export class ProductListComponent {
  onNotify() {
    window.alert('You will be notified when the product goes on sale');
  }
}
```
```
<app-product-alerts
  [product]="product" 
  (notify)="onNotify()">
</app-product-alerts>
```

## 添加导航
### 将 URL 路径与组件关联
在 app.module.ts 中，添加产品详细信息的路由，其中​​ path 为 products/:productId ， ProductDetailsComponent 为 component 。
```
@NgModule({
  imports: [
    BrowserModule,
    ReactiveFormsModule,
    RouterModule.forRoot([
      { path: '', component: ProductListComponent },
      { path: 'products/:productId', component: ProductDetailsComponent },
    ])
  ],
  declarations: [
    AppComponent,
    TopBarComponent,
    ProductListComponent,
    ProductAlertsComponent,
    ProductDetailsComponent,
  ],
```

修改产品名称锚点以包含 routerLink 和 product.id 作为参数。
```
<div *ngFor="let product of products">

  <h3>
    <a
      [title]="product.name + ' details'"
      [routerLink]="['/products', product.id]">
      {{ product.name }}
    </a>
  </h3>

  <!-- . . . -->

</div>
```

### 查看产品详情
```
import { ActivatedRoute } from '@angular/router';
```
```
export class ProductDetailsComponent implements OnInit {

  constructor(private route: ActivatedRoute) { }

}
```
```
ngOnInit() {
  const routeParams = this.route.snapshot.paramMap;
  const productIdFromRoute = Number(routeParams.get('productId'));
}
```

## 管理数据
### 创建购物车服务
在 Angular 中，服务是类的实例，您可以使用 Angular 的依赖注入系统将其提供给应用程序的任何部分。  

### 定义购物车服务
```
import { Product } from './products';
import { Injectable } from '@angular/core';
/* . . . */
@Injectable({
  providedIn: 'root',
})
export class CartService {
  items: Product[] = [];
  /* . . . */

  addToCart(product: Product) {
    this.items.push(product);
  }

  getItems() {
    return this.items;
  }

  clearCart() {
    this.items = [];
    return this.items;
  }
  /* . . . */
}
```

### 使用购物车服务
```
import { CartService } from '../cart.service';

export class ProductDetailsComponent implements OnInit {

  constructor(
    private cartService: CartService
  ) { }

  addToCart(product: Product) {
    this.cartService.addToCart(product);
    window.alert('Your product has been added to the cart!');
  }
}
```

### 创建购物车视图
略

### 显示购物车商品
略

### 检索运费
配置 AppModule 以使用 HttpClient：要使用 Angular 的 HttpClient ，您必须将应用程序配置为使用 HttpClientModule 。  
配置 CartService 以使用 HttpClient
```
@Injectable({
  providedIn: 'root'
})
export class CartService {
  items: Product[] = [];

  constructor(
    private http: HttpClient
  ) {}

  getShippingPrices() {
    return this.http.get<{type: string, price: number}[]>('/assets/shipping.json');
  }

/* . . . */
}
```

### 创建运输组件
配置 ShippingComponent 以使用 CartService
```
export class ShippingComponent implements OnInit {

  shippingCosts!: Observable<{ type: string, price: number }[]>;

  ngOnInit(): void {
    this.shippingCosts =  this.cartService.getShippingPrices();
  }

}
```

## 使用表单进行用户输入
### 定义结帐表单模型
```
import { FormBuilder } from '@angular/forms';

export class CartComponent {

  constructor(
    private formBuilder: FormBuilder,
  ) {}

  checkoutForm = this.formBuilder.group({
    name: '',
    address: ''
  });

  onSubmit(): void {
    // Process checkout data here
    this.items = this.cartService.clearCart();
    console.warn('Your order has been submitted', this.checkoutForm.value);
    this.checkoutForm.reset();
  }
}
```
### 创建结账表格
```
<h3>Cart</h3>

<p>
  <a routerLink="/shipping">Shipping Prices</a>
</p>

<div class="cart-item" *ngFor="let item of items">
  <span>{{ item.name }} </span>
  <span>{{ item.price | currency }}</span>
</div>

<form [formGroup]="checkoutForm" (ngSubmit)="onSubmit()">

  <div>
    <label for="name">
      Name
    </label>
    <input id="name" type="text" formControlName="name">
  </div>

  <div>
    <label for="address">
      Address
    </label>
    <input id="address" type="text" formControlName="address">
  </div>

  <button class="button" type="submit">Purchase</button>

</form>
```

## 部署应用程序
ng build 命令是用于将 Angular 应用源代码编译成可部署的生产环境代码的操作。

# 设置
## 设置本地环境和工作区
略

## 先决条件
略

## 安装 Angular CLI
```
npm install -g @angular/cli
```

## 创建工作区和初始应用程序
```
ng new my-app
```

## 运行应用程序
```
ng serve --open
```