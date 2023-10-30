# NgModules 简介
NgModules 配置注入器和编译器，并帮助将相关内容组织在一起。

NgModule 是由装饰器标记的 @NgModule 类。 @NgModule 采用一个元数据对象，该对象描述如何编译组件的模板以及如何在运行时创建注入器。它标识模块自己的组件、指令和管道，通过 exports 属性将它们中的一些公开，以便外部组件可以使用它们。 @NgModule 还可以将服务提供程序添加到应用程序依赖注入器。

## Angular 模块化
模块是组织应用程序并使用外部库中的功能对其进行扩展的好方法。

NgModules 将组件、指令和管道整合到有凝聚力的功能块中，每个功能块都专注于一个功能领域、应用程序业务域、工作流或通用实用程序集合。

模块可以在应用程序启动时急切加载，也可以由路由器异步延迟加载。

NgModule元数据执行以下操作：
* 声明哪些组件、指令和管道属于模块
* 将其中一些组件、指令和管道设为公共，以便其他模块的组件模板可以使用它们
* 使用当前模块中的组件所需的组件、指令和管道导入其他模块
* 提供其他应用程序组件可以使用的服务

每个 Angular 应用程序都至少有一个模块，即根模块。引导该模块以启动应用程序。根模块是您在组件很少的应用程序中所需要的全部内容。随着应用程序的增长，将根模块重构为表示相关功能集合的功能模块。然后，将这些模块导入到根模块中。

## 根基模块 NgModules
```
// imports
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppComponent } from './app.component';

// @NgModule decorator with its metadata
@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule {}
```

# JS Modules vs NgModules

# 使用根模块启动应用程序

# 常用 NgModules

# 功能模块的类型

# 功能模块

# 提供依赖

# 单例服务

# 共享 NgModules

# NgModules API

# NgModules 常见 FAQs