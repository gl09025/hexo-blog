---
title: 让WSL变得更好看
date: 2017-02-19 16:43:03
updated: 2018-01-09 02:19:04
tags: 
  - WSL
  - windows
categories:
  - 软件
thumbnail:
---
### 首先开启windows10上面的bash
[参考官方教程](https://msdn.microsoft.com/en-us/commandline/wsl/install_guide)

### wsl-terminal

安装比bash好用的终端软件
[wsl-terminal-github](https://github.com/goreliu/wsl-terminal)

### oh my zsh
[官网](http://ohmyz.sh/)
[Github](https://github.com/robbyrussell/oh-my-zsh)

我安装了agnoster主题，但安装完了默认的字体还是不支持这个主题，下载字体
[https://github.com/powerline/fonts/tree/master/DejaVuSansMono](https://github.com/powerline/fonts/tree/master/DejaVuSansMono)

我选择了DejaVu Sans Mono for Powerline.ttf字体，双击安装。

### 颜色
让终端颜色更好看
[Github](https://github.com/seebi/dircolors-solarized)

将仓库克隆下来，找个位置放一下。我就直接放在
```bash
~/Git
```
再执行这条语句
```bash
eval `dircolors ~/Git/dircolors-solarized/dircolors.256dark`
```


#### 安装nodejs和npm

```bash
sudo apt-get autoremove --purge npm node nodejs
curl -sL https://deb.nodesource.com/setup_7.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo npm install -g npm
```
运行 npm config set loglevel http，让你知道 npm 发的每一个请求
运行 npm config set progress false，关闭那个进度条
为了让你的安装速度变快，运行 npm config set registry https://registry.npm.taobao.org/想要恢复成原样，只需要 npm config delete registry 即可

##### npm i -g vue-cli 出错

```bash
$ npm install -g async
$ npm install -g abbrev
$ npm install -g http-errors
$ npm install -g browerify
$ npm i -g npm
```

>参考文章
>https://medium.com/@Andreas_cmj/how-to-setup-a-nice-looking-terminal-with-wsl-in-windows-10-creators-update-2b468ed7c326
