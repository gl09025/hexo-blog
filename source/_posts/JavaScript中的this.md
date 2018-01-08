---
title: JavaScript中的this
date: 2017-05-17 23:49:12
updated: 2018-01-09 02:19:04
tags: 
  - JS
categories:
  - 技术
thumbnail:
---

# 最简单的解释

this就是function.prototype.call()的第一个参数

# 第一个参数是什么
三种方法来确定call()的第一个参数
1.直接在控制台打出`console.log(this)`
2.查看查看源代码。
3.查看API文档

通常我们通过查看文档来理解，实际写代码中可以使用第一种方法来判断
比如jQuery的`.on()`的文档说明
```
当jQuery的调用处理程序时，this关键字指向的是当前正在执行事件的元素。对于直接事件而言，this 代表绑定事件的元素。对于代理事件而言，this 则代表了与 selector 相匹配的元素。(注意，如果事件是从后代元素冒泡上来的话，那么 this 就有可能不等于 event.target。)若要使用 jQuery 的相关方法，可以根据当前元素创建一个 jQuery 对象，即使用 $(this)。
```
再比如MDN关于this的一段文档
```
DOM事件处理函数中的 this

当函数被用作事件处理函数时，它的this指向触发事件的元素
```



分割线

# This在箭头函数中的应用

箭头函数不使用this的四种标准规则，而是根据外层（函数或者全局）作用域来决定this。

我们来看一下箭头函数的词法作用域：

```javascript
function foo() {
    // 返回一个箭头函数
    return (a) => {
        // this继承自foo()
        console.log(this.a)
    };
}

var obj1 = {
    a: 2
};

var obj2 = {
    a: 3
};

var bar = foo.call(obj1);
bar.call(obj2); // 2, 不是3！
```

foo()内部创建的箭头函数会捕获调用时foo()的this。由于foo()的this绑定到obj1，bar（引用箭头函数）的this也会绑定到obj1，箭头函数的绑定无法被修改。（new也不行!）

## 总结

> 如果要判断一个运行中的函数的this绑定，就需要找到这个函数的直接调用位置。找到之后就可以顺序应用下面这四条规则来判断this的绑定对象。
>
> 1. 由new调用？绑定到新创建的对象。
> 2. 由call或者apply（或者bind）调用？绑定到指定的对象。
> 3. 由上下文对象调用？绑定到那个上下文对象。
> 4. 默认：在严格模式下绑定到undefined，否则绑定到全局对象。

>参考资料
>http://www.jquery123.com/on/ 
>https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/this#DOM事件处理函数中的_this
>
>http://www.codeceo.com/article/about-javascript-this.html