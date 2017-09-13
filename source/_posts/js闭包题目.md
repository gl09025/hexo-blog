---
title: js闭包题目.md
date: 2017-9-13 15:33:17
tags: js
thumbnail:
---
>实现函数 makeClosures，调用之后满足如下条件：
>1、返回一个函数数组 result，长度与 arr 相同 <br>
>2、运行 result 中第 i 个函数，即 `result[i]()` ，结果与 `fn(arr[i])` 相同


## 题意理解
题目要求的是将数组的每一个元素都放到一个函数里，并且将数组元素当做函数的参数，这些函数放到一个数组里面，长度与现在的数组相同。
函数取名为makeClosures，接受两个参数，一个数组，一个函数。


## 编码
### 第一次想法
使用循环将每个函数push进新的数组,参数为传进来的数组的每一项。
```javascript
function makeClosures(arr,fn){
    var result =[]
    for (var i=0;i<arr.length;i++) {
        result.push(fn(arr[i])) //需要返回函数，不是执行结果
    }
    return result
}
```

上面的函数有一个问题，我们需要的是返回一个函数，但是`fn()` 就直接执行了，所以外面要包一层函数。

### 第二次想法

```javascript
function makeClosures(arr,fn){
    var result =[]
    for (var i=0;i<arr.length;i++) {
        result.push(function(){
            return fn(arr[i]) //得到最后一个i
        })
    }
    return result
}
```

这样闭包的话只能得到变量的最后一个值，就是最后得到的都是 `arr[arr.length]` 需要使用匿名函数通过参数将arr的每一项的值传递进去

### 第三次，最终结果

```javascript
function makeClosures(arr,fn){
    var result =[]
    for (var i=0;i<arr.length;i++) {
        result.push((function(num){
            return function(){
                return fn(num)
        }
        })(arr[i]))//匿名函数将数组每一项传给里面的函数
    }
    return result
}
```
### 测试结果

```javascript

function makeClosures(arr,fn){
    var result =[]
    for (var i=0;i<arr.length;i++) {
        result.push((function(num){
            return function(){
                return fn(num)
        }
        })(arr[i]))//匿名函数将数组每一项传给里面的函数
    }
    return result
}

var arr = [1, 2, 3, 4, 5];
var square = function (x) { return x * x; };
var funcs = makeClosures(arr, square); 
console.log(funcs)
console.log(funcs[0]()); // 1
console.log(funcs[1]()); // 4
console.log(funcs[2]()); // 9
console.assert(funcs[0]() === square(arr[0]))
```

## 另外一些写法

### 使用forEach

```javascript
function makeClosures(arr,fn){
    var result =[]
    arr.forEach(function(e){
        result.push(function(){
            return fn(e)
        }) 
    })
    return result
}
```

forEach()方法的参数就是每次循环的当前元素和i无关。

### 使用bind

```javascript
function makeClosures(arr,fn){
    var result =[]
    for (var i=0;i<arr.length;i++) {
        result.push(fn.bind(null,arr[i])) 
    }
    return result
}
```

### ES6的let

在上面第三步的时候换做使用let也可以保证传入i

```javascript
function makeClosures(arr,fn){
    var result =[]
    for (let i=0;i<arr.length;i++) { //使用let
        result.push(function(){
            return fn(arr[i])
        })
    }
    return result
}
```



参考链接
>[参考1-牛客网](https://www.nowcoder.com/questionTerminal/578026cd24e3446bbf27fe565473dc26) <br>
>[参考2-简书](http://www.jianshu.com/p/8dcb306399f0)