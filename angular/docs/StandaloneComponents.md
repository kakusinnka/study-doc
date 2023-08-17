# 独立组件
## 创建独立组件
### standalone 标志和组件 imports
组件、指令和管道现在可以标记为 standalone: true。标记为独立的 Angular 类不需要在 NgModule 中声明。  

### 在独立组件中使用现有的 NgModules
编写独立组件时，你可能希望在组件的模板中使用其他组件、指令或管道。其中某些依赖项可能不会标记为独立，而是由现有的 NgModule 声明和导出。在这种情况下，你可以将 NgModule 直接导入到独立组件中。

## 在基于 NgModule 的应用程序中使用独立组件
独立组件也可以导入到现有的基于 NgModules 的上下文中。这允许现有应用程序逐步采用新的独立风格的组件。

## 使用独立组件引导应用程序
通过使用独立组件作为应用程序的根组件，可以在没有任何 NgModule 的情况下引导 Angular 应用程序。这是使用 bootstrapApplication API 来完成的。

### 配置依赖注入
引导应用程序时，你通常希望配置 Angular 的依赖注入并提供配置值或服务以在整个应用程序中使用。你可以将这些作为提供者传递给 bootstrapApplication。

## 路由和惰性加载
路由器 API 进行了更新和简化，以利用独立组件的优势：在许多常见的惰性加载场景中不再需要 NgModule。

### 惰性加载独立组件
任何路由都可以用 loadComponent 惰性加载其路由到的独立组件。

### 一次惰性加载多个路由
loadChildren 操作现在支持加载一组新的子 Route，而无需编写惰性加载的 NgModule 来导入 RouterModule.forChild 来声明路由。

### 惰性加载和默认导出
使用 loadChildren 和 loadComponent 时，路由器会理解并使用 default 导出来自动解包动态 import() 调用。你可以利用这一点跳过 .then() 进行此类惰性加载操作。

### 
... 略并不理解

# 迁移到独立组件
还没有去理解
