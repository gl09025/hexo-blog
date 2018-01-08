---
title: 使用原生JS实现事件委托
date: 2017-04-17 22:03:02
updated: 2018-01-09 02:19:04
tags: 
  - JS
categories:
  - 技术
thumbnail: 
---
## 事件

在使用JavaScript与DOM交互时,事件是用到的比较多的.

JavaScript的事件机制是一个标准的观察者模式([Observer Pattern](https://zh.wikipedia.org/zh/%E8%A7%82%E5%AF%9F%E8%80%85%E6%A8%A1%E5%BC%8F)),是一种抽象的订阅者和开发者的模式.我们可以在节点上添加上指定条件下的触发事件.

## 事件绑定和事件监听

在DOM level 0中事件是直接绑定的,比如

```javascript
buttom.onclick = function(){}
```

到了DOM level 2的时候增加了事件监听,比如

```javascript
button.addEventListener('click',function(){})
```

事件绑定的方法有个缺点就是它只能绑定一次,而使用`addEventListener` 可以绑定多个函数,执行顺序按照绑定的先后顺序来执行.

在使用过程中发现,如果我们在需要的元素上都添加了监听,那这是非常消耗资源和性能的,所以才有了事件委托.

## 什么是事件委托

事件委托是为了避免我们在特定的每个节点上都添加事件监听器,而在父节点上来监听冒泡上来的事件.

事件委托是基于冒泡机制的,所以本篇重点关注冒泡阶段.浏览器的

### 冒泡

冒泡如下图所示,element2的事件先被触发,然后是element1

```
               / \
---------------| |-----------------
| element1     | |                |
|   -----------| |-----------     |
|   |element2  | |          |     |
|   -------------------------     |
|        Event BUBBLING           |
-----------------------------------
```



## 举例说明

以下的例子我们都使用`addEventListener` ,其中参数`e` 为浏览器传给我们的一个包含了事件各种属性的对象.

### 第一个例子

现在我们有一个需求,要在点击列表里面的时候在控制台打印出hello.

先写HTML,稍微加点样式	

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Test</title>
  <style>
    li{background-color: red;}
    ul{border: 20px solid green;}
  </style>
</head>
<body>
<ul>
  <li>one</li>
  <li>two</li>
  <li>three</li>
  <li>four</li>
</ul>
</body>
</html>
```

要在点击li的时候打出hello,

```javascript
var liName = document.querySelectorAll('li')
function fn(e){
  if(e.target.tagName === 'LI' ){ //target为当前点击的元素
    console.log('hello') 
    }
}
//在每个li上添加监听
liName[0].addEventListener('click',fn)
liName[1].addEventListener('click',fn)
liName[2].addEventListener('click',fn)
liName[3].addEventListener('click',fn)
```

每个元素上都添加监听是非常耗资源的,我们可以在li的父元素ul上添加一个监听事件

```javascript
var ulTest = document.querySelector('ul')
function fn(e){
  if(e.target.tagName === 'LI' ){
    console.log('hello') 
    }
}
//添加ul上的监听事件
ulTest.addEventListener('click',fn)
```

上面的代码同样可以达到同样的需求,而且占用的资源更少.



那么如果我们需要监听的元素不是li,而是li的子元素呢?

```html
......
<ul>
  <li><span>one</span></li>
  <li>two</li>
  <li>three</li>
  <li>four</li>
</ul>
......
```

改写:

```javascript
var ulTest = document.querySelector('ul')
var bodyTest = document.querySelector('body')
function fn(e){
  var el = e.target  
  while(el.tagName !== 'LI'){
    el = el.parentNode
  }
  if(el){
  console.log('hello')
  }else{
    console.log('111')
  }
}

//添加ul上的监听事件
ulTest.addEventListener('click',fn)
```

上面的代码中,点击li中的span,ul也能够出发监听事件.会在用户点击的元素一级一级的往上找(冒泡),找到符合条件的就调用事件.

### 第二个例子

在div中有p和h1,其中又各有一个span.我们需要在点击h1或h1里的span的时候触发事件.

```html

<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Test</title>
  <style>
    p{ background-color: red;}
    h1{ background-color: green;}
    span{ background-color: yellow;}
  </style>
</head>
<body>
<div>
  <p>我是<span>p</span></p>
  <h1>我是<span>h1</span></h1>
</div>
</body>
</html>
```



JS

```javascript
var div = document.querySelector('div')

div.addEventListener('click',function(e){
  var t = e.target
  //寻找H1节点
  while(t.tagName !== 'H1'){
    if(t === div){
      t = null
      break;
    }
    t = t.parentNode
  }
  if(t){
    console.log('你找到了h1')
  }else{
    console.log('你点击了其他元素')
  }
})
```

在上面的代码中,首先在最外层的div上添加监听事件,在while循环中我们判断当天的点击元素是否为H1元素,如果不是我们往上查找,直到查到H1元素.如果查到了最外层的div元素,证明没有在H1元素之内,我们就不需要再往上去查找了,所以这里我们将元素置为null.







## 参考

> http://pij.robinqu.me/Browser_Scripting/DOM_Scripting/EventAPI.html
>
> https://developer.mozilla.org/zh-CN/docs/Web/API/EventTarget/addEventListener
>
> https://www.quirksmode.org/js/events_order.html
>
> https://developer.mozilla.org/zh-CN/docs/Web/API/Event
>
> http://javascript.ruanyifeng.com/dom/event.html