# 概述
RxJS 是一个使用可观察序列编写异步和基于事件的程序的库。

RxJS 中解决异步事件管理的基本概念是：
* Observable：代表未来值或事件的可调用集合的想法。
* Observer: 是一个回调集合，它知道如何监听 Observable 传递的值。
* Subscription：代表 Observable 的执行，主要用于取消执行。
* Operators: 是纯函数，支持使用函数式编程风格处理集合，例如 map 、 filter 、 concat 、 reduce 、 等。
* subject：相当于EventEmitter，是向多个Observers多播一个值或事件的唯一方式。
* Schedulers: 是控制并发的集中调度程序，允许我们在计算发生时进行协调，例如 setTimeout 或 requestAnimationFrame 或其他。

### 纯度
优雅的处理异步事件, 再加上纯函数, 使得异步代码更优雅。

### 流动
RxJS 拥有一整套运算符，可以帮助您控制事件如何流经您的可观察对象。

### 值
您可以转换通过可观察量传递的值。

## Observable 可观察对象
Observables 是多个值的惰性 Push 集合。

### Pull versus Push
Pull 和 Push 是两种不同的协议，用于描述数据生产者如何与数据使用者进行通信。  
在 Pull 系统中，Consumer 决定何时从 Data Producer 接收数据。生产者本身不知道数据何时会交付给消费者。  
在推送系统中，生产者决定何时向消费者发送数据。消费者不知道何时会收到该数据。

Observable 是多个值的生产者，将它们“推送”给观察者（消费者）。

### 可观察对象作为函数的泛化
有些人声称 Observables 是异步的。事实并非如此。可观察对象能够同步或异步传递值。observable.subscribe() 表示“给我任意数量的值，无论是同步的还是异步的”  
Observable 和函数有什么区别？随着时间的流逝，可观察对象可以“返回”多个值，而函数则不能。  
func.call()意思是“同步给我一个值"  
observable.subscribe()意思是“给我任意数量的值，无论是同步的还是异步的"

### 可观察对象的剖析
核心可观察关注点：1, 创建可观察对象. 2, 订阅 Observables. 3, 执行可观察对象. 4, 释放可观察对象.

## Observer 观察者
观察者是 Observable 传递的值的消费者。 观察者只是一组回调，每个回调对应 Observable 传递的每种类型的通知：next 、error 和 complete。

## RxJS 运算符
运算符是必不可少的部分，它允许以声明性方式轻松编写复杂的异步代码。

### 什么是运算符？
运算符是函数。有两种类型的运算符：可管道运算符，创建性运算符。

### 可管道运算符
可管道运算符是函数，因此它们可以像普通函数一样使用。

### 创建性运算符
创建运算符是可用于创建具有一些常见预定义行为或通过连接其他可观察对象来创建 Observable 的函数。

### 高阶可观察对象
concatAll(), mergeAll() , switchAll() , exhaustAll()

### 弹珠图
略

### 运算符类别
创建运算符，合并创建运算符，转换运算符，筛选运算符，合并运算符，组播运算符，错误处理运算符，工具运营商，条件运算符和布尔运算符，数学运算符和聚合运算符，

### 创建自定义运算符
略

## Subscription 订阅
订阅是表示一次性资源的对象，通常是 Observable 的执行。订阅有一个重要的方法，即 unsubscribe ，它不带任何参数，只是释放订阅所持有的资源。

## Subject 主题
RxJS 主题是一种特殊类型的 Observable，它允许将值多播到多个 Observer。普通的 Observable 是单播的（每个订阅的 Observer 都拥有 Observable 的独立执行），而 Subject 是多播的。  
每个主题都是一个可观察对象。每个主体同时也都是一个观察者。

### 多播可观察对象
多播 Observable 在后台使用一个 Subject，使多个 Observer 看到相同的 Observable 执行。

#### 引用计数
略

### BehaviorSubject
主体的变体之一是 BehaviorSubject，它具有 “当前值” 的概念。它存储发送给其消费者的最新值，每当有新的观察者订阅时，它将立即从 BehaviorSubject 接收“当前值”。

### ReplaySubject
A ReplaySubject 记录 Observable 执行中的多个值，并将它们重播给新订阅者。

### AsyncSubject
AsyncSubject 类似于 last() 运算符，因为它等待 complete 通知以传递单个值。

### Void subject
略

## Scheduler 调度
Schedulers 提供了一种方式来管理 Observable 执行的时序，对于在不同上下文中执行代码、处理异步任务等情况非常有用。

## 弹珠测试
略

# 安装
# 导入
# 参考
# Operator 决策树
# 弃用和重大变更
# 详细变更清单
# 行为准则

# 参考
## [RxJS 官方文档](https://rxjs.dev/guide/overview)
## [RxJS](https://www.elialotti.com/en/roadmap/rxjs)