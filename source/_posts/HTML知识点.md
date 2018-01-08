---
title: HTML知识点
date: 2017-02-11 22:45:14
updated: 2018-01-09 02:19:04
tags: 
  - HTML
categories:
  - 技术
thumbnail:
---

## HTML、XML、XHTML有什么区别

HTML:全称为超文本标记语言(Hyper Text Markup Language)，是一种使用标记标签来描述网页的标记语言，不属于编程语言。
XML:全称为可扩展标记语言(Extensible Markup Language)被设计用来传输和存储数据的可扩展标记语言。不是HTML的替代，XML的侧重点在于数据的内容，而HTML的侧重点在数据的外观。
XHTML:全称为可扩展超文本标签语言(Extensible Hyper Text Markup Language)，基于XML并且比HTML更严格更纯净，是用来替代HTML的。



## 怎样理解HTML语义化

语义化就是要用正确的标签来做正确的事，使页面的内容结构化，语义化既可以容易阅读和维护，又便于对浏览器、搜索引擎解析。

## 内容与样式分离的原则
### 原则
- 写 HTML 的时候先不管样式, 重点放在HTML的结构和语义化上，让 HTML 能体现页面结构或者内容。之后再去写样式。
- HTML 内不允许出现属性样式，尽量不要出现行内样式。
### 使用这个原则的原因
- 提高机器可读性，让浏览器能够更好的去解析页面结构。
- 当需要修改网页内容时，省时，效率。样式和内容分离查找起来更容易。
- 样式可以根据不同的浏览器来做兼容。保证网页显示效果的统一。

## 有哪些常见的meta标签

meta常用于定义页面的说明，关键字，最后修改日期和其他元数据。这些元数据将服务于浏览器(如何布局或重载页面)，搜索引擎和其他网络服务。
常见的标签：

```markup
<meta name="keywords" content="网页关键字">
<meta name="description" content="网页的主要内容">
<meta name="author" content="作者名字，作者邮箱">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1">
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
<meta charset="urf-8">
```
[这里有更详细的解释](https://segmentfault.com/a/1190000004279791)


## 文档声明的作用？严格模式和混杂模式指什么？<!doctype html>的作用？

<!doctype html>代表 文档对象模型，作用是告诉浏览器使用html5的方式来解析渲染当前的页面。
没有这个文档声明的话，浏览器会根据的自己的方式去解析渲染当前的页面，有可能会造成样式和内容渲染的效果不一样，这时候就是混杂模式了。有了文档声明就是严格模式，浏览器会按照所声明的格式来解析和渲染。

## 浏览器乱码的原因是什么？如何解决

乱码主要是因为编写页面文件后，在保存的时候编码和浏览里识别的编码不一样。
解决方法：在页面中声明为保存的编码，比如保存的编码为`utf-8`，在页面中也声明为这个编码。
```markup
<meta charset="utf-8">
```

## 常见的浏览器有哪些？什么内核？

Chrome、Opera、safari都为webkit内核。
Firefox为Gecko内核。
[更详细的内核介绍](http://web.jobbole.com/84826/)

## 列出常见的标签，并简单介绍这些标签用在什么场景

### head
定义文档的头部，它是所有头部元素的容器。里面可以引用脚本、指示浏览器在哪里找到样式表、提供元信息等等。
```markup
<head></head>
```
### body
定义文档的主题，包含文档的所有内容(比如文本、超链接、图像、表格和列表等等)。
```markup
<body></body>
```
### 标题h1~h6
定义标题从大到小依次为h1,h2,h3,h4,h5,h6。
```markup
<h1>标题1</h1>
<h2>标题2</h2>
......
```
### 文本强调
主要用于强调特定的内容。
#### strong
表示强调标签文本内容，不改变其含义。
```markup
<strong></strong>
```
#### em
表示感情上的强调，增强了语气。
```markup
<strong>Text</strong>
<em>Text</em>
```
### 段落和块
`p`和`div`p是语义化的段落标签，用于文章分段；div是普通的块标签，多用于布局。
```markup
<p></p>
<div></div>
```

### 图片
用于嵌入图像。
```markup
<img src="图像url" alt="图像的替代文本">
```
### 超链接
用于链接到另一个页面。
```markup
<a href="url">文本</a>
```
### 按钮
定义一个按钮。
```markup
<button >按钮</button>
```

### 有序列表
定义一个有序列表。
```markup
<ol>
    <li>1</li>
    <li>2</li>
</ol>
```
### 无序列表
定义无序列表。
```markup
<ul>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
```

### 表格
定义一个简单的HTML表格。
```markup
<table border="1">
  <tr>
    <th>Month</th>
    <th>Savings</th>
  </tr>
  <tr>
    <td>January</td>
    <td>$100</td>
  </tr>
</table>
```

>参考链接
>[HTML语义化](https://leohxj.gitbooks.io/front-end-database/html-and-css-basic/semantic-html.html)
>[XML简介](http://w3school.com.cn/xml/xml_intro.asp)
>[HTML简介](http://w3school.com.cn/html/html_intro.asp)
>[XHTML简介](http://w3school.com.cn/xhtml/xhtml_intro.asp)



