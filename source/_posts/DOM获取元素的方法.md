---
title: DOM获取元素的方法
date: 2017-04-17 23:28:47
updated: 2018-01-09 02:19:04
tags: 
  - JS
  - DOM
categories:
  - 技术
thumbnail:
---

操作DOM时我们经常需要获取元素,这里总结一下获取元素的方法

| 方法名                                    | 参数       | 特点     |
| -------------------------------------- | -------- | ------ |
| document.getElementById(id)            | ID       | 返回单个对象 |
| document.getElementsByClassName(names) | class名称  | 返回集合   |
| document.getElementsByName(name)       | 元素name属性 | 返回集合   |
| document.getElementsByTagName(tagName) | 标签名      | 返回集合   |
| document.querySelector(selectors)      | CSS选择器   | 返回单个对象 |
| document.querySelectorAll(selectors)   | CSS选择器   | 返回集合   |

---------------------------------------

## document.getElementById()

返回一个匹配特定 [ID](https://developer.mozilla.org/en-US/docs/DOM/element.id)的元素.

### 语法

> element = document.getElementById(id)

### 参数

> - `element是一个` [Element](https://developer.mozilla.org/en-US/docs/DOM/element) 对象。如果当前文档中拥有特定ID的元素不存在则返回null.
> - `id是大小写敏感的字符串，代表了所要查找的元素的唯一ID`.

### 示例

```html
<!DOCTYPE html>
<html>
<head>
  <title>getElementById example</title>
  <script>
  function changeColor(newColor) {
    var elem = document.getElementById("para1");
    elem.style.color = newColor;
  }
  </script>
</head>
<body>
  <p id="para1">Some text here</p>
  <button onclick="changeColor('blue');">blue</button>
</body>
</html>
```



## document.getElementsByClassName()

返回一个类似数组的对象，包含了所有指定 class 名称的子元素。当调用发生在document对象上时, 整个DOM都会被搜索, 包含根节点。你也可以在任意元素上调用[`getElementsByClassName()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/getElementsByClassName) 方法，它将返回的是以当前元素为根节点，所有指定class名称的子元素。

### 语法

>   var elements = document.getElementsByClassName(names); // or:                                                                                var elements = rootElement.getElementsByClassName(names);

### 参数

> - elements 是查找到的所有元素的集合 [`HTMLCollection`](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLCollection) .
> - names 是一个字符串，表示用于匹配的 class 名称列表; class 名称通过空格分隔
> - getElementsByClassName 可以在任意的元素上调用，不仅仅是 document。 调用这个方法的元素将作为本次查找的根元素.

### 示例

```javascript
document.getElementsByClassName('test');
document.getElementsByClassName('red test'); //class同时包括red和test
document.getElementById('main').getElementsByClassName('test'); //在id 为'main'的元素的子节点中，获取所有class为'test'的元素
```

## document.getElementsByName()

根据给定的[`name`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/name) 返回一个在 (X)HTML document的节点列表集合。

### 语法

> ```
> elements = document.getElementsByName(name) 
> ```

### 参数

> - `elements` 是一个 [`NodeList`](https://developer.mozilla.org/zh-CN/docs/Web/API/NodeList) 集合。
> - `name` 是元素的 `name` 属性的值。

### 示例

```html
<!DOCTYPE html>
<html lang="en">
<head>
 ...
</head>

<body>
<form name="up"><input type="text"></form>
<div name="down"><input type="text"></div>

<script>
var up_forms = document.getElementsByName("up");
console.log(up_forms[0].tagName); // returns "FORM"
</script>
</body>
</html>
```

## document.getElementsByTagName()

返回带有指定标签名的对象的集合.

### 语法

> ```
> elements = element.getElementsByTagName(tagName)
> ```

### 参数

> `tagName` 必须放在引号中

### 示例

```html
<!DOCTYPE html>
<html>
<head>
...
</head>
<body>
<ul><li>Coffee</li><li>Tea</li></ul>
<p id="demo">单击“按钮”更改列表项的文本。</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var list=document.getElementsByTagName("UL")[0]
	list.getElementsByTagName("LI")[0].innerHTML="Milk";
};
</script>
</body>
</html>
```

## document.querySelector()

querySelector() 方法返回文档中匹配指定 CSS 选择器的一个元素。

### 语法

> ```
> element = document.querySelector(selectors)
> ```

### 参数

> selectors: css选择器

### 示例

```html
  //获取文档中第一个 <p> 元素：
  document.querySelector("p")
  //获取文档中 class="example" 的第一个元素:
  document.querySelector(".example");
  //获取文档中 class="example" 的第一个 <p> 元素:
  document.querySelector("p.example");
  //获取文档中有 "target" 属性的第一个 <a> 元素：
  document.querySelector("a[target]");
  
```



## document.querySelectorAll()

### 语法

> ```
> elementList = document.querySelectorAll(selectors);
> ```



### 参数

> 获取的是一个集合
>
> selectors为css选择器

### 示例

```javascript
//返回一个文档中所有的class为"note"或者 "alert"的div元素
var matches = document.querySelectorAll("div.note, div.alert");
```





