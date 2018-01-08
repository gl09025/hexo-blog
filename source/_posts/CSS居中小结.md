---
title: CSS居中小结
date: 2017-03-22 14:26:53
updated: 2018-01-09 02:19:04
tags: 
  - CSS
  - README
categories:
  - 技术
thumbnail:
---
最近在学习CSS居中,居中里面又包含水平居中和垂直居中,分不太清内联元素(inline or inline-* elements)和块元素(block level element)居中到底应该怎么来居中,记住一个忘了另一个.翻译一篇CSS-TRICKS上的居中完全指南来理清自己的思绪.

[内联元素有哪些](https://developer.mozilla.org/en-US/docs/Web/CSS/display#Values)

[块元素有哪些](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)



## 水平居中

### 内联或者内联相关元素(像text或者links)

在块级别的父元素中添加`text-align: center;` 属性

[在线示例](http://js.jirengu.com/gosa/5/watch?html,css,output)

![内联元素水平居中](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E5%86%85%E8%81%94%E5%85%83%E7%B4%A0%E6%B0%B4%E5%B9%B3%E5%B1%85%E4%B8%AD.png)

### 块元素

在自身CSS中添加属性`margin: 0 auto;` 这个就相当于`margin-left: auto;` `margin-right: auto;` ,当然这里有一个宽度才能看到效果,当块元素没有宽度的时候,会自动铺满整行.

[在线示例](http://js.jirengu.com/gosa/3/watch?html,css,output)

![块元素水平居中](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E5%9D%97%E5%85%83%E7%B4%A0%E6%B0%B4%E5%B9%B3%E5%B1%85%E4%B8%AD.png)

注意:我们不能让有`float` 属性的元素居中



### 多个块元素居中

如果现在有两个或以上的块元素,我们又需要在一行上居中.我们就可以使用`display` 来转换成其他类型.比如我们这里变成`inline-block` 或变成flexbox

[在线示例](http://js.jirengu.com/gosa/2/watch?html,css,output)

![多个块级元素在一行居中](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E5%A4%9A%E4%B8%AA%E5%9D%97%E7%BA%A7%E5%85%83%E7%B4%A0%E5%9C%A8%E4%B8%80%E8%A1%8C%E5%B1%85%E4%B8%AD.png)

当多个块级元素占不同行的时候,也可以时间居中.

[在线示例](http://js.jirengu.com/bewi/2/watch?html,css,output)

![多个块级元素不在一行水平居中](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E5%A4%9A%E4%B8%AA%E5%9D%97%E7%BA%A7%E5%85%83%E7%B4%A0%E4%B8%8D%E5%9C%A8%E4%B8%80%E8%A1%8C%E6%B0%B4%E5%B9%B3%E5%B1%85%E4%B8%AD.png)



## 垂直居中

垂直居中比水平居中要复杂.

### 内联或者内联相关元素(像text或者links)

#### 单行

当单行内联元素有上下相等的padding的时候,可以垂直居中.

[在线示例](http://js.jirengu.com/gosa/7/watch?html,css,output)

![垂直居中-单行内联元素](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD-%E5%8D%95%E8%A1%8C%E5%86%85%E8%81%94%E5%85%83%E7%B4%A0.png)

如果padding因为某种原因不能改,有个小技巧是设置`line-height` 和`height` 一样来达到垂直居中的效果.

[在线示例](http://js.jirengu.com/gosa/8/watch?html,css,output)

![垂直居中-块内有文字](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD-%E5%9D%97%E5%86%85%E6%9C%89%E6%96%87%E5%AD%97.png)



#### 多行

给定上下的padding一样可以作用于多行的文本,如果没有起作用的话,可能这个元素里面的文字类型是table cell.我们可以使用`vertical-align` 来处理

[在线示例](http://js.jirengu.com/jeya/1/watch?html,css,output)

![垂直居中-table cell](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD-flexbox.png)

现在貌似使用table已经不推荐使用了,那我们可以使用flexbox,用flexbox就十分的easy了.设置如下属性就行

```css
.flex-center-vertically {
  display: flex;
  justify-content: center;
  flex-direction: column;
  height: 400px;
}
```

[在线示例](http://js.jirengu.com/hoke/1/watch?html,css,output)

![垂直居中-flexbox](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD-%E5%88%A9%E7%94%A8before%E4%BC%AA%E5%85%83%E7%B4%A0.png)

上面的flex实现的垂直居中是在父元素有固定高度的情况下生效的.

如果上面两个方法都不流行了的话,那我们还可以使用"ghost element",就是我们说的伪元素

```css
.ghost-center {
  position: relative;
}
.ghost-center::before {
  content: " ";
  display: inline-block;
  height: 100%;
  width: 1%;
  vertical-align: middle;
}
.ghost-center p {
  display: inline-block;
  vertical-align: middle;
}
```

[在线示例](http://js.jirengu.com/rohiz/1/watch?html,css,output)

![垂直居中-利用before伪元素](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD-%E5%9D%97%E5%85%83%E7%B4%A0-%E6%9C%89%E9%AB%98%E5%BA%A6.png)



### 块元素

#### 知道元素的高度

一般我们不会设置高度,因为当宽度变化的时候,里面的文本内容会去自动改变父元素的高度.文字样式的变化可以改变高度.文字数量的变化可以改变高度.有固定长宽比的元素比如图像可以在调整大小时改变高度.等等.

如果我们知道高度的话可以这么写

```css
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  height: 100px;
  margin-top: -50px; /* account for padding and border if not using box-sizing: border-box; */
}
```

[在线示例](http://js.jirengu.com/gede/1/watch?html,css,output)

![垂直居中-块元素-有高度](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD-%E5%9D%97%E5%85%83%E7%B4%A0-%E6%9C%89%E9%AB%98%E5%BA%A6.png)

#### 不知道元素的高度

我们仍然可以用定位来实现

```css
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}
```

[在线示例](http://js.jirengu.com/rata/1/watch?html,css,output)

![垂直居中-块元素-不知道高度](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD-%E5%9D%97%E5%85%83%E7%B4%A0-%E4%B8%8D%E7%9F%A5%E9%81%93%E9%AB%98%E5%BA%A6.png)

#### 使用flexbox? 

使用flexbox就比较简单了

```css
.parent {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
```

[在线示例](http://js.jirengu.com/wapu/1/watch?html,css,output)

![垂直居中-块级元素-flexbox](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD-%E5%9D%97%E7%BA%A7%E5%85%83%E7%B4%A0-flexbox.png)

## 水平和垂直居中

我们可以结合上面的水平居中和垂直居中来完成水平和垂直的同时居中.通常有以下三种情况

### 有固定的高度和宽度的元素

知道宽高的情况下我们一般需要算一下距离上面和左边多少,使用定位来实现.

[在线示例](http://js.jirengu.com/yoyi/1/watch?html,css,output)

![水平垂直居中-固定宽高比](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E6%B0%B4%E5%B9%B3%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD-%E5%9B%BA%E5%AE%9A%E5%AE%BD%E9%AB%98%E6%AF%94.png)

### 无固定高度和宽度的元素

不知道宽高,我们也使用定位来实现,这次我们就不需要计算距离,使用50%的translate来实现

``` CSS
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

[在线示例](http://js.jirengu.com/vanom/1/watch?html,css,output)

![水平垂直居中-无固定宽高比](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E6%B0%B4%E5%B9%B3%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD-%E6%97%A0%E5%9B%BA%E5%AE%9A%E5%AE%BD%E9%AB%98%E6%AF%94.png)

### 方便的flexbox

```css
.parent {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

[在线示例](http://js.jirengu.com/jomi/1/watch?html,css,output)

![水平垂直居中-flexbox](https://raw.githubusercontent.com/gl09025/blog/master/images/CSSjuzhongxiaojie/%E6%B0%B4%E5%B9%B3%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD-flexbox.png)

##  小结

看到了这么多,发现使用flex是最方便的.关于flexbox的兼容性我们可以[点击这里](http://caniuse.com/flexbox)看到.现在我们在写网页的时候能不带宽高的就尽量不要带宽高.