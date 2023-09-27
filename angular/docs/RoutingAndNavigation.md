# 概述
在单页应用程序中，您可以通过显示或隐藏与特定组件相对应的显示部分来更改用户所看到的内容，而不是前往服务器获取新页面。当用户执行应用程序任务时，他们需要在您定义的不同视图之间移动。

要处理从一个视图到下一个视图的导航，可以使用 Angular Router 。 Router 通过将浏览器 URL 解释为更改视图的指令来启用导航。

# 常见路由任务
## 生成启用路由的应用程序
```
ng new routing-app --routing --defaults
```

### 添加路由组件
```
ng generate component first
ng generate component second
```

### 导入您的新组件
略

## 定义基本路由
创建路由由三个基本构建块组成。  
将 AppRoutingModule 导入 AppModule 并将其添加到 imports 数组中。

1. 将 RouterModule 和 Routes 导入您的路由模块。
2. 在 Routes 数组中定义您的路线。
3. 将您的路线添加到您的应用程序中。

### 路线顺序
路由的顺序很重要，因为 Router 在匹配路由时使用首匹配获胜策略，因此更具体的路由应该放在不太具体的路由之上。首先列出具有静态路径的路由，然后列出与默认路由匹配的空路径路由。通配符路由排在最后，因为它匹配每个 URL，并且仅当没有其他路由首先匹配时 Router 才会选择它。

## 获取路线信息
> 不懂

## 设置通配符路由
两个星号 ** 向 Angular 指示此 routes 定义是通配符路由。对于组件属性，您可以定义应用程序中的任何组件。常见的选择包括特定于应用程序的 PageNotFoundComponent ，您可以定义它来向用户显示 404 页面；或重定向到应用程序的主要组件。通配符路由是最后一个路由，因为它可以匹配任何 URL。

## 显示 404 页面
最后一条 path 为 ** 的路由是通配符路由。如果请求的 URL 与列表中前面的任何路径都不匹配，则路由器会选择此路由并将用户发送到 PageNotFoundComponent 。

## 设置重定向
略

## 嵌套路线
子路由与任何其他路由一样，它需要 path 和 component 。一个区别是您将子路由放置在父路由内的 children 数组中。

## 设置页面标题
应用程序中的每个页面都应该有一个唯一的标题，以便可以在浏览器历史记录中识别它们。 Router 使用 Route 配置中的 title 属性设置文档的标题。
> 了解的比较浅

## 使用相对路径
使用 ../ 表示法向上一级。使用 ./ 或不使用前导斜杠来指定当前级别。
> 了解的比较浅

## 访问查询参数和片段
> 不懂

## [延迟加载](https://angular.io/guide/lazy-loading-ngmodules)
您可以将路由配置为延迟加载模块，这意味着 Angular 仅根据需要加载模块，而不是在应用程序启动时加载所有模块。此外，在后台预加载应用程序的某些部分以改善用户体验。

## [防止未经授权的访问](https://angular.io/guide/router-tutorial-toh#milestone-5-route-guards)
使用路由防护来防止用户未经授权导航到应用程序的某些部分。

## 链接参数数组
```html
    <li>
      <!-- 动态路由绑定 带一个变量 -->
      <a [routerLink]="[dynamicRouterLink]" routerLinkActive="hzh-active3">Second Component</a>
    </li>
    <li>
      <!-- 动态路由绑定 带多个变量 -->
      <a [routerLink]="[dynamicRouterLink, '1', '2' ]" routerLinkActive="hzh-active4">Second Component</a>
    </li>
    <li>
      <!-- 动态路由绑定 带参数 -->
      <a [routerLink]="[dynamicRouterLink + '/param', { foo1: 'abc', foo2: 'def' } ]"
        routerLinkActive="hzh-active5">Second Component</a>
    </li>
```

## LocationStrategy 和浏览器 URL 样式
当路由器导航到新的组件视图时，它会使用该视图的 URL 更新浏览器的位置和历史记录。
> 似懂非懂

## 选择路由策略
> 这是在说啥

## <base href>
您必须将 <base href> 元素添加到应用程序的 index.html 中， pushState 路由才能正常工作。当引用 CSS 文件、脚本和图像时，浏览器使用 <base href> 值作为相对 URL 的前缀。
> 似懂非懂

# 在单页应用程序中使用 Angular 路由
在单页应用程序 (SPA) 中，应用程序的所有功能都存在于单个 HTML 页面中。当用户访问应用程序的功能时，浏览器只需要呈现对用户重要的部分，而不是加载新页面。此模式可以显着改善应用程序的用户体验。

## 目标
* 将示例应用程序的功能组织到模块中。
* 定义如何导航到组件。
* 使用参数将信息传递给组件。
* 通过嵌套多个路由来构建路由。
* 检查用户是否可以访问该路由。
* 控制应用程序是否可以放弃未保存的更改。
* 通过预取路线数据和延迟加载功能模块来提高性能。
* 需要特定的标准来加载组件。

## 先决条件
略

## 创建示例应用程序
略

## 从 @angular/router 导入 RouterModule
略

## 定义您的路线
略

## 使用 router-outlet 更新您的组件
略

## 使用 UI 元素控制导航
略

## 识别活动路由
略

## 添加重定向
略

## 添加 404 页面
略

# 教程：创建自定义路由匹配
Angular Router 支持强大的匹配策略，您可以使用它来帮助用户导航您的应用程序。该匹配策略支持静态路由、带参数的可变路由、通配符路由等。此外，还可以针对 URL 较为复杂的情况构建您自己的自定义模式匹配。

## 目标
* 实现 Angular 的 UrlMatcher 来创建自定义路由匹配器。

## 先决条件
略

## 
