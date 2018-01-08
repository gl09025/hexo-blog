---
title: HTML-Form知识点小结
date: 2017-02-12 21:56:18
updated: 2018-01-09 02:19:04
tags: 
  - HTML
categories:
  - 技术
thumbnail:
---
## 1.form表单有什么作用？有哪些常用的input标签，分别有什么作用

主要用于将页面上用户填写的信息提交给网站后台服务器，达到向服务器传输数据的目的。常用的input标签:`text` 、`password` 、`radio` 、`checkbox` 、`file` 、`textarea` 、`image`、`button`、`submit`、`reset`  

| 值        | 描述                                 |
| :------- | :--------------------------------- |
| text     | 定义单行的输入字段，用户可在其中输入文本。默认宽度为20个字符。   |
| password | 定义密码字段。该字段中的字符被掩码。                 |
| radio    | 定义单选按钮。                            |
| checkbox | 定义复选框。                             |
| file     | 定义输入字段和“浏览”按钮，供文件上传。               |
| image    | 定义图像形式的提交按钮。                       |
| button   | 定义可点击按钮（多数情况下，用于通过JavaScript启动脚本）。 |
| submit   | 定义提交按钮。提交按钮会把表单数据发送到服务器。           |
| reset    | 定义重置按钮。重置按钮会清除表单中的所有数据。            |

## 2.post和get方式的区别？

- 传送方式。
    get请求是会将表单数据以明文附在URL之后，在实际开发中特定的浏览器和服务器对于URL的长度是有限制的。post提交的数据放在HTTP消息主体中，不会改变URL的长度。
- 安全
    post的安全性要比get高。get在发送数据是会将数据拼接到url上是明文的。
- URL长度数据量。
    get会将数据放置在url上，所以url更长。而post不会改变当前的url。

一般我们在进行不重要的数据传输是可以使用get，比如搜索引擎。在设计敏感信息时我们应该使用POST。

## 3.在input里，name有什么作用？

主要是对提交到服务区后的表单数据进行标识，只有设置了name属性的表单元素才能在提交表单时传递他们的值。

## 4.radio如何分组？

设置`name`属性中的值为一样。例如：

```markup
<input type="radio" name="sex" value="male"/>男
<input type="radio" name="sex" value="female"/>女
```

## 5.placeholder属性有什么作用？

在可描述的`input`标签中提供一个预览信息以供提示。该提示会在输入字段为空时显示，在获得焦点后消失。适用于以下`input`类型:text、search、url、telephone、email以及password。

## 6.type=hidden隐藏域有什么作用？举例说明

基本语法：

```markup
<input type="hidden" name="country" value="China" />
```
定义为hidden是用户不可见的，会存储一个默认值，用于暂存数据和提高安全。
1.有时候我们要给用户一些信息，让他在提交表单时提交上来以确定用户身份。
2.一个网页中有多个form时，可以分别在form中写隐藏域来更好的区分。


