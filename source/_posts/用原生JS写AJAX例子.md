---
title: 用原生JS写AJAX例子
date: 2017-07-21 10:54:37
tags: JS
---
## AJAX

[MDN_AJAX](https://developer.mozilla.org/zh-CN/docs/AJAX/Getting_Started)

手写AJAX的主要四个步骤：
1.创建XMLHttpReauest
2.处理响应（指定响应函数）
3.打开链接（指定请求）
4.发送请求

```javascript
<button id="ajaxButton" type="button">Make a request</button>

<script>
(function() {
  var httpRequest;
  document.getElementById("ajaxButton").addEventListener('click', makeRequest);//按钮添加点击事件

  function makeRequest() {
    httpRequest = new XMLHttpRequest();//创建XMLHttpRequest对象

    if (!httpRequest) {
      alert('Giving up :( Cannot create an XMLHTTP instance');
      return false;
    }
    httpRequest.onreadystatechange = alertContents;//指定相应函数
    httpRequest.open('GET', 'test.html');//打开链接
    httpRequest.send();//发送请求
  }

  function alertContents() {
    if (httpRequest.readyState === XMLHttpRequest.DONE) {
      if (httpRequest.status === 200) {
        alert(httpRequest.responseText);
      } else {
        alert('There was a problem with the request.');
      }
    }
  }
})();
</script>
```