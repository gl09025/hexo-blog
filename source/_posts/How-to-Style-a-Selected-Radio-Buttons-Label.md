---
title: How to Style a Selected Radio Buttons Label
date: 2017-07-26 15:00:59
tags: CSS
thumbnail:
---
选中radio按钮改变样式

<a class="jsbin-embed" href="http://jsbin.com/katemofega/2/embed?output">JS Bin on jsbin.com</a><script src="http://static.jsbin.com/js/embed.min.js?4.0.4"></script>

[效果演示](http://jsbin.com/katemofega/2/edit?html,css,output)

```markup
<div class="radio-toolbar">
  <input type="radio" id="radio1" name="radios" value="all" checked>
  <label for="radio1">All</label>

  <input type="radio" id="radio2" name="radios" value="false">
  <label for="radio2">Open</label>

  <input type="radio" id="radio3" name="radios" value="true">
  <label for="radio3">Archived</label>
</div>
```

主要是用到一个CSS选择器`+` 
B + E ：元素B的任一下一个兄弟元素E

```css
    .radio-toolbar input[type="radio"] {
      display: none;
    }

    .radio-toolbar label {
      display: inline-block;
      background-color: #ddd;
      padding: 4px 11px;
      font-family: Arial;
      font-size: 16px;
      cursor: pointer;
    }

    .radio-toolbar input[type="radio"]:checked+label {
      background-color: #bbb;
    }
```


