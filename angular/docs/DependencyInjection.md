# Angular 中的依赖注入
依赖注入或 DI 是一种设计模式和机制，用于创建应用程序的某些部分并将其传递到需要它们的应用程序的其他部分。Angular 支持这种设计模式，你可以在应用程序中使用它来提高灵活性和模块化程度。

# 解依赖注入
## 了解依赖注入
略

## 提供依赖
第一步是添加 @Injectable 装饰器以表明该类可以被注入。
```
@Injectable()
class HeroService {}
```

下一步是通过提供它来使其在 DI 中可用。可以在多个地方提供依赖项：  
在组件级别，使用 @Component 装饰器的 providers 字段。在这种情况下， HeroService 可供该组件以及模板中使用的其他组件和指令的所有实例使用。例如：
```
@Component({
  selector: 'hero-list',
  template: '...',
  providers: [HeroService]
})
class HeroListComponent {}
```
当您在组件级别注册提供程序时，您会通过该组件的每个新实例获得该服务的一个新实例。

在 NgModule 级别，使用 @NgModule 装饰器的 providers 字段。
```
@NgModule({
  declarations: [HeroListComponent]
  providers: [HeroService]
})
class HeroListModule {}
```

在应用程序根级别，允许将其注入到应用程序中的其他类中。这可以通过将 providedIn: 'root' 字段添加到 @Injectable 装饰器来完成：
```
@Injectable({
  providedIn: 'root'
})
class HeroService {}
```
当您在根级别提供服务时，Angular 会创建 HeroService 的单个共享实例，并将其注入到任何需要它的类中。

## 注入依赖
注入依赖项的最常见方法是在类构造函数中声明它。
```
@Component({ … })
class HeroListComponent {
  constructor(private service: HeroService) {}
}
```

另一种选择是使用注入方法：
```
@Component({ … })
class HeroListComponent {
  private service = inject(HeroService);
}
```

当 Angular 发现组件依赖于某个服务时，它首先检查注入器是否具有该服务的任何现有实例。如果请求的服务实例尚不存在，注入器将使用注册的提供者创建一个实例，并将其添加到注入器，然后将服务返回给 Angular。

# 创建可注入服务
## 服务实例
略

## 创建可注入服务
略

## 注入服务
略

## 在其他服务中注入服务
略

# 配置依赖提供者
## 指定提供者令牌
在以下示例中， Logger 服务类提供了一个 Logger 实例。
```
providers: [Logger]
```

扩展的提供程序配置是一个具有两个属性的对象文字：
```
[{ provide: Logger, useClass: Logger }]
```
* provide 属性保存令牌，该令牌充当查找依赖项值和配置注入器的密钥。
* 第二个属性是提供者定义对象，它告诉注入器如何创建依赖值。提供者定义键可以是以下之一：
  * useClass - 此选项告诉 Angular DI 在注入依赖项时实例化提供的类
  * useExisting - 允许您为令牌添加别名并引用任何现有令牌。
  * useFactory - 允许您定义构造依赖项的函数。
  * useValue - 提供应用作依赖项的静态值。

## 类提供者：useClass
useClass 提供程序键允许您创建并返回指定类的新实例。您可以使用这种类型的提供程序来替换公共或默认类的替代实现。
```ts
{ provide: Logger, useClass: BetterLogger }
```
如果替代类提供程序有自己的依赖项，请在父模块或组件的提供程序元数据属性中指定这两个提供程序。
```ts
[ UserService,
  { provide: Logger, useClass: EvenBetterLogger }]
```

## 别名提供者：useExisting
useExisting 提供程序密钥可让您将一个令牌映射到另一个令牌。实际上，第一个令牌是与第二个令牌关联的服务的别名，创建了两种访问同一服务对象的方式。
```ts
[ NewLogger,
  // 别名 OldLogger 并引用 NewLogger
  { provide: OldLogger, useExisting: NewLogger}]
```

## 工厂提供者：useFactory
useFactory 提供程序键允许您通过调用工厂函数来创建依赖项对象。通过这种方法，您可以根据 DI 和应用程序其他位置中的可用信息创建动态值。

## 值提供者：useValue
useValue 键可让您将固定值与 DI 令牌关联起来。使用此技术提供运行时配置常量，例如网站基地址和功能标志。

## 使用 InjectionToken 对象
在 Angular 中，InjectionToken 是一种用于创建注入令牌的类，它是依赖注入系统的一部分，用于将值或依赖项注入到组件、指令、服务等中。与普通的字符串令牌不同，InjectionToken 提供了更强大的类型安全性和可维护性。

## 接口和 DI
当转译器将 TypeScript 更改为 JavaScript 时，接口就会消失，因为 JavaScript 没有接口。

# 注入上下文
搞不懂

# 多级注入器
搞不懂