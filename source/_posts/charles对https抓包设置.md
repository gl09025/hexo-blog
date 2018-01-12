---
title: charles对https抓包设置
date: 2018-01-12 00:37:32
updated: 2018-01-12 00:37:37
tags: 
  - charles
  - capture
categories:
  - 技术
thumbnail:
---

> charles在对https网站进行抓包时请求里的很多都是乱码，网上查询了是需要安装charles的证书，但我在macOS sierra上安装时遇到了一个错误。。。

# 安装证书

help->ssl proxying->install charles root certificate
![install charles root cerrificate](https://raw.githubusercontent.com/gl09025/image_respository/master/2018%E5%B9%B401%E6%9C%8812%E6%97%A5/install%20charles%20root%20cerrificate.png)

会遇到以下错误
![cannotbemodified](https://raw.githubusercontent.com/gl09025/image_respository/master/2018%E5%B9%B401%E6%9C%8812%E6%97%A5/cannotbemodified.png)

遇到这个错误，我查了四五十分钟，没什么结果，其实报错信息很明显，就是不能在“System Roots”里面安装证书，只能在login里安装证书。（论学好英语的重要性 <img src="http://www.webpagefx.com/tools/emoji-cheat-sheet/graphics/emojis/expressionless.png" height="20" width="20" align="absmiddle">）

## 解决办法

1.保存charles的证书
  ![https://raw.githubusercontent.com/gl09025/image_respository/master/2018%E5%B9%B401%E6%9C%8812%E6%97%A5/cannotbemodified.png](https://raw.githubusercontent.com/gl09025/image_respository/master/2018%E5%B9%B401%E6%9C%8812%E6%97%A5/savecharlesrootcertificate.png)

2.在keychain access里安装
    将上面保存的证书拖到login里,右键证书选择 get info
    ![gitinfo](https://raw.githubusercontent.com/gl09025/image_respository/master/2018%E5%B9%B401%E6%9C%8812%E6%97%A5/gitinfo.png)

3.在trust里选择永久信任
    ![alwaystrust](https://raw.githubusercontent.com/gl09025/image_respository/master/2018%E5%B9%B401%E6%9C%8812%E6%97%A5/alwaystrust.png)
    输入密码确认

至此证书就安装完毕了。

# 设置ssl proxy settings

![choosesslproxyingsettings](https://raw.githubusercontent.com/gl09025/image_respository/master/2018%E5%B9%B401%E6%9C%8812%E6%97%A5/choosesslproxyingsettings.png)

我在这里添加了默认所有443端口都抓包
![sslproxysetting](https://raw.githubusercontent.com/gl09025/image_respository/master/2018%E5%B9%B401%E6%9C%8812%E6%97%A5/sslproxysetting.png)

保存之后就可以对https网站抓包了。

# chrome代理扩展处理

当你的chrome安装了代理软件，比如 'SwitchyOmega' 需要让网站走charles，要不然是抓不到包的。
需要添加一条charles的代理，如下图
![switchyomega-charles](https://raw.githubusercontent.com/gl09025/image_respository/master/2018%E5%B9%B401%E6%9C%8812%E6%97%A5/switchyomega-charles.png)

然后对网站应用这个代理，就能抓到包了。