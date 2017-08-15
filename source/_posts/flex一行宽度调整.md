---
title: 表单提交与阻止默认动作
date: 2017-08-15 12:42:42
tags: CSS
thumbnail:
---

使用flex布局。
在一行中有四个元素等宽排列。
我们这样写

```markup
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>flex等宽排列</title>
  <style>
    .flex {
      display: flex;
      text-align: center;

    }

    .flex div{
      width: 25%;
      border: 1px solid #ddd;
    }

  </style>
</head>
<body>
<div class="flex">
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
</div>
</body>
</html>
```

<a class="jsbin-embed" href="http://jsbin.com/gopufax/embed?output">flex等宽排列 on jsbin.com</a><script src="http://static.jsbin.com/js/embed.min.js?4.0.4"></script>

使用flex后就简单的设置每个元素的宽度为25%就可以了。

## 给其中一个改变比例

现在如果需求是需要将第二个改为35%我们该怎么写CSS呢？
还是利用flex的一些属性，flex-grow,flex-shrink

```markup
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>flex等宽排列，变动其中一个</title>
  <style>
    .flex {
      display: flex;
     text-align: center;

    }

    .flex div{
      flex-basis: 25%;
      border: 1px solid #ddd;
    }

    .flex div:nth-child(2) {
      flex-basis: 55%;
    }
  </style>
</head>
<body>
<div class="flex">
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
</div>
</body>
</html>
```

<a class="jsbin-embed" href="http://jsbin.com/jovubes/embed?output">flex等宽排列，变动其中一个 on jsbin.com</a><script src="http://static.jsbin.com/js/embed.min.js?4.0.4"></script>

设置每个元素的flex-basis为25%, flex-basis 指定了 flex 元素在主轴方向上的初始大小。
然后设置第二个的flex-basis为需求比例。就有效果了
