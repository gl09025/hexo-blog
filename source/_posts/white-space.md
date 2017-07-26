---
title: white-space
date: 2017-06-01 15:04:43
tags: CSS   
thumbnail:
---
white-space CSS 属性是用来设置如何处理元素中的空白。
### 语法
Formal syntax: normal | pre | nowrap | pre-wrap | pre-line
white-space: normal
white-space: nowrap
white-space: pre
white-space: pre-wrap
white-space: pre-line

normal
  连续的空白符会被合并，换行符会被当作空白符来处理。填充line盒子时，必要的话会换行。
nowrap
  和 normal 一样，连续的空白符会被合并。但文本内的换行无效。
pre
  连续的空白符会被保留。在遇到换行符或者<br>元素时才会换行。 
pre-wrap
  连续的空白符会被保留。在遇到换行符或者<br>元素，或者需要为了填充line盒子时才会换行。
pre-line
  连续的空白符会被合并。在遇到换行符或者<br>元素，或者需要为了填充line盒子时会换行。

|          | 换行符  | 空格和制表符 | 文字转行 |
| -------- | :--- | :----- | ---- |
| normal   | 合并   | 合并     | 转行   |
| nowrap   | 合并   | 合并     | 不转行  |
| pre      | 保留   | 保留     | 不转行  |
| pre-wrap | 保留   | 保留     | 转行   |
| pre-line | 保留   | 合并     | 转行   |




> 参考
> https://developer.mozilla.org/en-US/docs/Web/CSS/white-space?v=example
> [white-space](https://css-tricks.com/almanac/properties/w/whitespace/)

