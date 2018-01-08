---
title: MarkDown介绍
date: 2017-02-09 23:45:25
updated: 2018-01-09 02:19:04
tags: 
  - Markdown
categories:
  - 技术
thumbnail:
---

> Markdown已经成为Github圈内所共同使用并认可的编写文档语言

#什么是Markdown
Markdown是一种用来写作的轻量级的**标记语言**。何为标记语言，简单点理解就是一种以纯文字符号来表示成文本的相关信息，比如我们熟知的HTML。

#为什么要用Markdown
## 跨平台
标记语言是纯文本的，所以理论上只需一个系统自带的文本编辑器就可以来书写。如果要获得更舒适的体验还是需要安装相应平台对应的Markdown编辑器或者能够解析markdown语法的网页。


## 共同协作
因为有了全平台（Windows、Linux、OS X）通用的特性，所以换了环境也可以无缝的编写，无需额外的学习成本。通过GitHub平台可以很方便的进行多人协作。
## 排版便利
只需要用少量的文本符号就能够展现页面，具体见文章后半部分的常用语法。
## 拥护者众多
诞生于互联网时期的Markdown，受到GitHub圈极客们的热捧。能够改变世界的程序员们发明了Markdown来解决繁杂又耗时间的文档排版问题，毕竟时间就是金钱。
# 怎么使用Markdown

## 流行的编辑器

- web全平台
  [作业部落](https://www.zybuluo.com/)
- windows平台
  [MarkdownPad](http://www.markdownpad.com/)
- OS X平台
  [Mou](http://25.io/mou/)
- Linux平台
  [ReText](http://sourceforge.net/p/retext/home/ReText/)

## 常用语法
_**需要注意的是符号都是英文状态下的符号**_ <br />
这里只列出经常用到的一些语法。
### 标题
最多支持6级标题
![](http://upload-images.jianshu.io/upload_images/4122870-0d915662d0a3eb8f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 列表
在前面加`-`或者数字`1`


![Markdown有序列表.png](http://upload-images.jianshu.io/upload_images/4122870-b3b09688ef7ce395.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![Markdown无序列表.png](http://upload-images.jianshu.io/upload_images/4122870-bd9774094f956ddd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 链接和图片
两者的区别在于图片前多一个`!`符号

![Markdown链接.png](http://upload-images.jianshu.io/upload_images/4122870-3107d593132b6be7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

图片一般都为静态图片,可以上传到GitHub后获取图片的链接或使用其他图床。

![](http://upload-images.jianshu.io/upload_images/4122870-a447b285e5331210.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 引用

引用在前面添加`>`符号

![](http://upload-images.jianshu.io/upload_images/4122870-66fab7e7e064bea2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 字体强调

在字体的前后添加`**`或`_`来使字体变成粗体或斜体

![](http://upload-images.jianshu.io/upload_images/4122870-d997dba4b85d5453.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 代码块


![Markdown代码块.png](http://upload-images.jianshu.io/upload_images/4122870-e54f7707750d2ea7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 表格
代码
```
| 我是标题 | 我是标题 | 我是标题 |
| ------| ------ | ------ |
| 短文本 | 中等文本 | 稍微长一点的文本 |
| 稍微长一点的文本 | 短文本 | 中等文本 |
```
| 一个普通标题   | 一个普通标题 | 一个普通标题   |
| -------- | ------ | -------- |
| 短文本      | 中等文本   | 稍微长一点的文本 |
| 稍微长一点的文本 | 短文本    | 中等文本     |

相关代码
```
| 左对齐标题 | 右对齐标题 | 居中对齐标题 |
| :------| ------: | :------: |
| 短文本 | 中等文本 | 稍微长一点的文本 |
| 稍微长一点的文本 | 短文本 | 中等文本 |
```
| 左对齐标题    | 右对齐标题 |  居中对齐标题  |
| :------- | ----: | :------: |
| 短文本      |  中等文本 | 稍微长一点的文本 |
| 稍微长一点的文本 |   短文本 |   中等文本   |

简单语法介绍到这里，更详细的语法或高级语法可以参考一下链接
>[Markdown语法说明（简体中文版）](http://wowubuntu.com/markdown/)
>[Markdown 语法手册 （完整整理版）](http://blog.leanote.com/post/freewalk/Markdown-%E8%AF%AD%E6%B3%95%E6%89%8B%E5%86%8C)
>[Cmd Markdown 编辑阅读器- 作业部落出品](https://www.zybuluo.com/mdeditor?url=http://www.zybuluo.com/static/editor/md-help.markdown)


本文参考链接
[Markdown: Syntax](https://daringfireball.net/projects/markdown/syntax)<br />
[好用的Markdown编辑器一览](http://www.williamlong.info/archives/4319.html)<br />
[Markdown——入门指南](http://www.jianshu.com/p/1e402922ee32#)<br />
[Markdown写作浅谈](http://www.jianshu.com/p/PpDNMG)<br />
