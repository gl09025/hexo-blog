---
title: vim粘贴缩进
date: 2017-9-12 18:24:14
updated: 2018-01-09 02:19:04
tags: 
  - VIM
categories:
  - 技术
thumbnail:
---

解决办法：
1. 在拷贝前输入:set paste (这样的话，vim就不会启动自动缩进，而只是纯拷贝粘贴）
2. 拷贝完成之后，输入:set nopaste (关闭paste)