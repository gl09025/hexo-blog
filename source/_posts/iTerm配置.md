---
title: iTerm配置
date: 2017-12-10 17:26:47
updated: 2018-01-09 02:19:04
tags: 
  - iTerm2
  - mac
categories:
  - 软件
thumbnail:
---
# Mac下iTerm配置
## 安装iTerm
[官方网站](http://www.iterm2.com/)
下载并安装
## 配置iTerm
快捷键呼出（guake-like）
在Preferences - keys - Create aDedicated Hotkey Window...
添加一个新快捷键，默认配置，点击ok
![create a Dedicated Hotkey Windo](https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B412%E6%9C%8810%E6%97%A5/create%20a%20Dedicated%20Hotkey%20Window.png)

然后到 Preferences - Profiles下会看到新增的配置，可参考下图配置
![Hotkey Window -iTer](https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B412%E6%9C%8810%E6%97%A5/Hotkey%20Window%20-iTerm.png)
我这里设置为从顶部弹出 Full-Width Top of Screen.效果如下(图中是配置完oh-my-zsh的效果)
![top of screen](https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B412%E6%9C%8810%E6%97%A5/top%20of%20screen.png)

### zsh
* 安装
Mac 系统自带了 Zsh, 一般不是最新版，如果需要最新版可通过 Homebrew 来安装，没有Homebrew的，去[Homebrew官网](https://brew.sh/)安装
`brew install zsh`

* 设置默认shell为zsh
`chsh -s $(which zsh)`

* 重启命令行
使用如下命令来检查是否安装成功
`echo $SHELL`
有zsh字样出来就成功了

> [英文安装教程](https://github.com/robbyrussell/oh-my-zsh/wiki/Installing-ZSH)

### 赏心悦目的终端
![oh my zsh](https://camo.githubusercontent.com/5c385f15f3eaedb72cfcfbbaf75355b700ac0757/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6f686d797a73682f6f682d6d792d7a73682d6c6f676f2e706e67)
**注意：**安装oh-my-zsh之前必须安装zsh
[oh-my-zsh官网](http://ohmyz.sh/)

* oh-my-zsh目录结构
> lib 提供了核心功能的脚本库
> tools 提供安装、升级等功能的快捷工具
> plugins 自带插件的存在放位置
> templates 自带模板的存在放位置
> themes 自带主题文件的存在放位置
> custom 个性化配置目录，自安装的插件和主题可放这里

配置文件路径，主要就是在这里进行配置
`~/.zshrc`

* 设置主题
`ZSH_THEME="robbyrussel"`主题可以自己选择，可以到themes目录查看，然后替换这里双引号里面的主题名字即可。

* 插件
默认插件
`plugins=(git)`
要启用插件就要在括号中添加插件名字
`plugins=(git history-substring-search)
`
这里推荐几个插件
> [https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins/history-substring-search](zsh-history-substring-search)
> 
> [https://github.com/zsh-users/zsh-syntax-highlighting](zsh-syntax-highlighting
)
>
> [https://github.com/zsh-users/zsh-autosuggestions](zsh-autosuggestions
)

更多插件
> https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins
> https://github.com/unixorn/awesome-zsh-plugins
> https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins-Overview


## 参考文档
> https://www.hi-linux.com/posts/54879.html
> http://www.dreamxu.com/mac-terminal/
> http://wdxtub.com/2016/02/18/oh-my-zsh/

