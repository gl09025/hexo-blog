---
title: JS 小知识整理
date: 2018-02-04 21:45:04
updated: 2018-02-04 21:45:09
tags: 
  - JS
categories:
  - 技术
thumbnail:
---

## setTimeout

![](https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B411%E6%9C%8811%E6%97%A5/setTimeout.png)

为什么第一个跟第二个输出的不一样呢？

因为`setTimeout(fn, time)` **这里的fn必须是个函数**。

`function fn(){return function(){}}  setTimeout(fn(), 1000)` 这里会立即执行fn把执行的结果作为setTimeout的参数。

第一个由于是立即执行函数，所以就相当于普通的流输出的，不能当做setTimeout的参数。

## 数组去重

最简短的数组去重

es5
```javascript
[1,2,3,1,'a',1,'a'].filter(function(ele,index,array){
    return index===array.indexOf(ele)
})
```

es6
```javascript
[1,2,3,1,'a',1,'a'].filter((ele,index,array) => index===array.indexOf(ele))
```

es6
```javascript
[...new Set([1,2,3,1,'a',1,'a'])]
```

