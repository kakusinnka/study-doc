# 异步 JavaScript
JavaScript异步编程的历史可以追溯到早期的JavaScript语言，其发展主要受到Web的演变和需要处理异步任务的要求的影响。以下是JavaScript异步编程历史的主要里程碑：
1. 早期的JavaScript：JavaScript最初是一种单线程的脚本语言，用于处理网页上的简单交互和表单验证。在早期，JavaScript主要用于响应用户的事件，例如单击、鼠标移动等。
2. XMLHttpRequest：在2000年，XMLHttpRequest对象的引入为JavaScript引入了异步通信的能力。这使得浏览器可以通过AJAX（Asynchronous JavaScript and XML）技术向服务器发送HTTP请求，并在后台接收和处理数据。这是JavaScript异步编程的一个重要转折点。
3. 回调函数：随着异步操作的增多，JavaScript开始广泛使用回调函数来处理异步任务的结果。这导致了回调地狱（Callback Hell），其中多个嵌套的回调函数使代码难以阅读和维护。
4. Promise对象：为了解决回调地狱问题，ECMAScript 6（ES2015）引入了Promise对象，它提供了更具结构的方式来处理异步操作。Promise允许将异步任务链接在一起，以获得更清晰的代码结构。
5. async/await：ECMAScript 2017（ES2017）引入了async/await语法，进一步简化了异步编程。async函数允许在函数前面加上async关键字，以表示函数将返回一个Promise。await关键字用于等待Promise的解决，使代码看起来更像同步代码。
6. Generator函数：Generator函数是ES2015引入的另一种异步编程技术。它允许在函数执行期间暂停和恢复，以处理异步任务。
7. Web Workers：Web Workers是一种浏览器提供的多线程机制，用于在后台执行任务，以避免阻塞主线程。这使得JavaScript能够更好地处理多任务和CPU密集型操作。
8. 浏览器API和Node.js：浏览器和Node.js环境提供了许多异步API，用于处理文件I/O、网络请求、数据库访问等。这些API通常使用回调、Promise或async/await进行编程。
9. 现代前端框架和库：现代前端框架和库（如React、Angular、Vue.js）通常提供了更高级别的抽象，以简化异步编程和状态管理。它们使用虚拟DOM、单向数据流等概念来处理异步操作。

JavaScript异步编程的历史经历了多个阶段，从最初的事件处理到XMLHttpRequest、Promise、async/await等现代工具的引入。这些工具和技术的不断演化使得JavaScript能够更好地应对现代Web应用程序的需求，实现更好的性能和用户体验。

## 概述：异步 JavaScript

## 异步 JavaScript 简介
异步编程是一种技术，它使程序能够启动可能长时间运行的任务，并且仍然能够在该任务运行时响应其他事件，而不必等到该任务完成。完成该任务后，程序将收到结果。

### 事件处理程序 (Event handlers)
### 回调函数
1. 通过调用函数启动长时间运行的操作。
2. 让该函数启动操作并立即返回，以便我们的程序仍然可以响应其他事件。
3. 当操作最终完成时，将操作结果通知我们。

这正是异步函数可以做到的。

## 如何使用 promises
Promise 是现代 JavaScript 中异步编程的基础。promise 是由异步函数返回的对象，它表示操作的当前状态。在将 promise 返回给调用方时，操作通常尚未完成，但 promise 对象提供了处理操作最终成功或失败的方法。

### 使用 fetch() API
全局的 fetch() 方法用于发起获取资源的请求。它返回一个 promise，这个 promise 会在请求响应后被 resolve，并传回 Response 对象。

> 使用 fetch() API 来练习 Promise 非常合适

### async 和 await
有点像 Promise 的语法糖

## 如何实现基于 Promise 的 API
讨论了 Promise 的构造函数

## workers 简介
需要注意 worker.postMessage() 和 postMessage() 函数的用法

## 序列动画
一个帮助你练习 Promise 的例子

## 参照文献
### 1. [异步 JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous)
### 2. [JavaScript 异步编程的演变](https://blog.logrocket.com/evolution-async-programming-javascript/)

