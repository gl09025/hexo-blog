---
title: 使用Travis CI持续部署Hexo博客
date: 2017-02-08 14:24:05
tags: [Hexo,Travis CI]
thumbnail:
---
## 思路

将Hexo源码和发布代码放到一个仓库的不同分支，便于一一对应，也是对博客源码的备份。这里我使用Github Pages来展示自己的博客，并指定自定义域名。
使用Travis的配置，当仓库push后自动部署，不用手动发布。

## 整体流程

### 一个仓库两个分支

 1.新建仓库，为了方便我们可以将仓库名命名为 username.github.io，其中username是你的github的id，可以在右上角查看，图中红圈处。如果是使用自定义域名的话，其实仓库名称可以随便取名，为了方便我们不要随便取名。创建仓库的时候我们初始一个readme文件，这样方便我们新建分支操作。
 ![github_id](https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B47%E6%9C%8826%E6%97%A5/%E4%BD%BF%E7%94%A8Travis%20CI%E6%8C%81%E7%BB%AD%E9%83%A8%E7%BD%B2Hexo%E5%8D%9A%E5%AE%A2/github_id.png)
 2.创建一个新分支，这里不再赘述怎么创建新分支。例如我创建的新分支：blog-source
 3.现在我们有两个分支，一个默认的master分支，一个blog-source分支。blog-source分支用来存放我们的源码，master是部署后的文件。将blog-source设置为默认分支。在仓库的 settings->Branches->Default branch中设置。
 4.将仓库clone到本地
 5.在本地安装Hexo，具体安装步骤和配置在下文。
 6.Hexo配置好了之后，第一次我们先手动部署，`hexo d` 。（如果你集成了Travis就不需要手动部署了，只需要`git push` 就行了。）

这样我们就有两个分支了一个源码分支和一个部署分支。换了电脑我们只要将仓库克隆下来就可以操作了，配置文件也不会丢失。日常操作流程：`git add .`  `git commit -v` ` git push`  `hexo g -d`

### Github Pages

仓库的settings中开启Github Pages

![githubpages_open](https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B47%E6%9C%8826%E6%97%A5/%E4%BD%BF%E7%94%A8Travis%20CI%E6%8C%81%E7%BB%AD%E9%83%A8%E7%BD%B2Hexo%E5%8D%9A%E5%AE%A2/githubpages_open.png)

开启之后如果你的仓库名就是 username.github.io的话，就可以直接访问这个地址预览你的博客了。

### 自定义域名

首先你要有自己的域名，域名怎么注册呢？有很多选择，有[GoDaddy](https://sg.godaddy.com/zh/)，[阿里云](https://wanwang.aliyun.com/) ，[华夏名网](http://www.sudu.cn/)等等。
如果使用的是国外的域名注册商的话可以使用DNSPod的免费服务来接管域名注册商的DNS解析。这样国内会快一点。

在仓库中填上自定义域名
![githubpages_cunstomdomain](https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B47%E6%9C%8826%E6%97%A5/%E4%BD%BF%E7%94%A8Travis%20CI%E6%8C%81%E7%BB%AD%E9%83%A8%E7%BD%B2Hexo%E5%8D%9A%E5%AE%A2/githubpages_cunstomdomain.png)

在域名解析网站后台添加CNAME解析
![dns_cname]https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B47%E6%9C%8826%E6%97%A5/%E4%BD%BF%E7%94%A8Travis%20CI%E6%8C%81%E7%BB%AD%E9%83%A8%E7%BD%B2Hexo%E5%8D%9A%E5%AE%A2/dns_cname.png

**重要的一步**，我们要在你的Hexo仓库的source文件夹下添加名为`CNAME` 的文件，注意全部大写，里面内容就写你的自定义域名。如果没有这个文件，每次推送自定义域名都会回到初始的username.github.io

### Hexo安装和配置

参照官方文档来初始化一个Hexo项目

```bash
$ hexo init <folder>
$ cd <folder>
$ npm install
```
后面的配置参照官方文档的说明来定制自己的配置。[官方文档](https://hexo.io/zh-cn/docs/index.html)

一般我们都是找到自己喜欢的[主题](https://hexo.io/themes/)，然后配置主题。
常用的hexo命令
```
hexo g//生成静态文件
hexo s//开启本地server预览
hexo d//部署
```


### Travis

其实配置很简单，我们在官网使用github账号授权登录，hexo添加配置文件就可以了。
1.登录[官网](https://www.travis-ci.org/)，使用github账号登录。
2.添加仓库，这里我使用过所以会有，一些选项
![travis_addrespositories](https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B47%E6%9C%8826%E6%97%A5/%E4%BD%BF%E7%94%A8Travis%20CI%E6%8C%81%E7%BB%AD%E9%83%A8%E7%BD%B2Hexo%E5%8D%9A%E5%AE%A2/travis_addrespositories.png)

3.选中博客仓库
![travis_choose](https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B47%E6%9C%8826%E6%97%A5/%E4%BD%BF%E7%94%A8Travis%20CI%E6%8C%81%E7%BB%AD%E9%83%A8%E7%BD%B2Hexo%E5%8D%9A%E5%AE%A2/travis_choose.png)
4.设置选项
![travis_settings](https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B47%E6%9C%8826%E6%97%A5/%E4%BD%BF%E7%94%A8Travis%20CI%E6%8C%81%E7%BB%AD%E9%83%A8%E7%BD%B2Hexo%E5%8D%9A%E5%AE%A2/travis_settings.png)
5.在github添加Access Token，在右上角账号的settings->Personal access tokens.点击generate new token来生成新token
选择仓库权限就可以。
![github_accesstoken](https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B47%E6%9C%8826%E6%97%A5/%E4%BD%BF%E7%94%A8Travis%20CI%E6%8C%81%E7%BB%AD%E9%83%A8%E7%BD%B2Hexo%E5%8D%9A%E5%AE%A2/github_accesstoken.png)
生成之后一定要保存好，因为只会出现一次，丢失了就只能再重新生成了。

6.回到Travis官网，在设置中填入刚复制的token，取一个名字，这个名字需要写到下面的配置文件中。
![travis_addenvironment](https://raw.githubusercontent.com/gl09025/image_respository/master/2017%E5%B9%B47%E6%9C%8826%E6%97%A5/%E4%BD%BF%E7%94%A8Travis%20CI%E6%8C%81%E7%BB%AD%E9%83%A8%E7%BD%B2Hexo%E5%8D%9A%E5%AE%A2/travis_addenvironment.png)

7.在你的hexo博客源码中添加配置文件`.travis.yml`
你需要修改的是git的配置信息。
**要使用https协议的仓库地址，使用ssh仓库地址会失败。**
注意这一行`git push --force --quiet "https://${githubblog}@${GH_REF}"` 中的githubblog就是你刚在token那里取的名字，要对应上
```yaml
language: node_js
node_js: stable

# S: Build Lifecycle
install:
  - npm install


#before_script:
 # - npm install -g gulp

script:
  - hexo g

after_script:
  - cd ./public
  - git init
  - git config user.name "ganli"
  - git config user.email "gl09025@gmail.com"
  - git add .
  - git commit -m "Update docs"
  - git push --force --quiet "https://${githubblog}@${GH_REF}" master:master
# E: Build LifeCycle

branches:
  only:
    - blog-resource
env:
 global:
   - GH_REF: github.com/gl09025/hexo-blog.git
```
配置完成后推送到仓库中，我们就能看到网站中在部署了。