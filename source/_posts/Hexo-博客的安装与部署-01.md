---
title: Hexo-博客的安装与部署-01
date: 2022-07-28 19:14:42
tags: Hexo
categories: Hexo系列
type: categories
description: 软件环境 Git Node.js Clash for Windows(任意加速器，保证能连接到Github),然后Hexo博客初始化,最后我们会将搭建好的Hexo上传到Github
---

# 一. 软件环境
```
Git
Node.js
Clash for Windows(任意加速器，保证能连接到Github)
```
## 1.1 Git官网
我们会将搭建好的Hexo上传到Github，所以需要Git命令行支持。
Git官网页面[](1231233332132)
## 1.2 Node.js
Node官网页面[]()
快捷安装()
如果你的网络无法进行下载，请访问以下链接进行下载：
Git-密码0625-来自上杉九月的网盘分享
https://cloud.sakurasep.club/s/YdiE
Node.js-密码0625-来自上杉九月的网盘分享
https://cloud.sakurasep.club/s/jdHB
## 1.3 检查安装是否成功
打开cmd命令行，输入`node -v`后显示版本号，即为安装成功
在电脑的任意目录点击右键，能够显示Git Bash Here
使用这个功能可以更方便的在当前目录启动命令行，当然你也可以使用cmd的cd命令到当前目录

# 二. 博客本地化部署
## 2.1 更改npm为cnpm源
国内某些网络环境访问npm会出现问题，建议使用taobao镜像源，能有效减少故障的发生
cnpm切换过程
使用cnpm -v后正常输出版本号，即为安装成功
显示版本号
## 2.2 安装hexo命令行
全局安装`hexo`
```
npm install hexo-cli
or
yarn add hexo-cli
```
## 2.3 Hexo博客初始化
选取一个想要安装Hexo的目录，路径中最好不要含有中文，后续会更好处理
此时文件夹内应有初始化文件，不过只要接下来能够成功运行
如果初始化出现问题，即在运行hexo init的时候报错(通常是由于网络而出现问题)
如果出现网络问题导致无法下载，请访问以下链接获取基础包：
Hexo_基础包文件-密码0625-来自上杉九月的网盘分享
```
https://cloud.sakurasep.club/s/Nouy
```
## 2.4 运行博客
在博客根目录右键打开`Git Bash Here`

输入以下指令`hexo clean` 清除已经部署的网页静态文件

`hexo g` 编译当前博客
`hexo s` 启动本地服务器

出现`Hexo is running at http://localhost:4000/ . Press Ctrl+C to stop` 并且没有后续的警告语句，说明部署成功，在浏览器中输入localhost:4000查看部署效果。

如果你的端口4000被占用，可以使用hexo s -p 端口号。然后访问http://localhost:端口号

以上，博客的最基本的本地化部署已经完成，接下来的内容是将博客部署到网络进行在线访问。

# 三. 博客部署到网络
基本介绍一下目前不同部署方式的差别。

`Github`：微软旗下的开源代码托管平台，国内某些运营商可能无法访问，一般来说还是推荐部署在`Github Pages`，这也是我本人目前主要用的服务。
`Gitee`：虽然是国内的代码托管平台，访问速度可以保证，但是它的`Pages`页面需要手动更新，并且不能够绑定自定义的域名(如果你想和别的博主交换友链，最好还是要有一个域名。因为一般有域名的博客更有动力维护下去)。

`Coding`：部署方式很复杂，新版的`Coding Pages`貌似是和腾讯云挂钩，按量付费，感觉没必要了。

`Vercel`：是一个静态网页部署平台，好像访问速度要比`Github`稍微快一些，并且提供修改自定义域名。

云服务器：访问速度很大程度上取决于你的服务器的带宽，而且现在服务器的价格也不便宜，以后部署其他需要服务器的项目时再使用比较好。

## 3.1 部署到Github(推荐)
作为全球最大同性社交平台，我们主要讲部署到gitHub,其他的自行学习

### 3.1.1 创建Github仓库
注册完成Github账号，新建仓库用于保存上传博客代码。

`Tips`:试试新建一个仓库名为你`Github`用户名的仓库

新建仓库，```确保仓库为公开(Public)，并且仓库名与用户名保持一致,``` 其他设置正常，创建仓库。

### 3.1.2 获取与Github的连接（可跳过）
在任意位置打开`Git Bash Here`，输入以下指令` `
输入第三个命令后只需要连续按下三次回车，就会在C:\Users\用户名\.ssh中生成密钥文件

打开id_rsa.pub，复制文件内容，添加到`SSH`公钥
然后在`Git Bash`中输入以下命令测试是否连通`Github`

### 3.1.3 上传博客到Github
首先在`Git Bash`中输入以下命令安装部署插件

打开根目录下的_config.yml文件
```
代码
```
repo 可以复制此处的链接

填好后在`Git Bash`中输入下列命令部署到`Github`仓库

此时访问`https://Github用户名.github.io`即可访问

### 3.1.4 绑定自定义域名
你可以自行选择域名提供商，购买完域名后，在域名解析里设置以下解析记录

主机记录：设置为@为泛解析，即访问域名为`https://域名`。如果想要设置为二级域名，请将主机记录设置为想要设置的名称，比如主机记录设置为hexo，即访问域名为`https://hexo.域名`

记录类型：设置为`CNAME`，将域名解析到网址。因为`Github`建议将自定义域名以CNAME解析到Github用户名.github.io

然后在`_config.yml`中设置`url`为你解析的域名
最后再博客根目录/source下新建CNAME文件

用于Github识别项目的自定义地址

## 3.2 部署到Gitee(备用方法)
Gitee官网
### 3.2.1 创建Gitee仓库
部署到`Gitee`与部署到`Github`的流程相差很小，看一个就行。

### 3.2.2 获取与Gitee的连接
在任意位置打开`Git Bash Here`，输入以下指令
获取`SSH`公钥

输入第三个命令后只需要连续按下三次回车，就会在C:\Users\用户名\.ssh中生成密钥文件

用记事本打开`id_rsa.pub`，复制文件内容，添加到`SSH`公钥

然后在`Git Bash`中输入以下命令测试是否连通`Gitee`

连接成功

### 3.2.3 上传博客到Gitee
首先在`Git Bash`中输入以下命令安装部署插件
打开根目录下的`_config.yml`文件最后部分
```
deploy:
  type: git
  repo: https://github.com/txw1314/txw1314.github.io.git
  branch: master
```
repo 后面是仓库链接(我的是：`https://github.com/txw1314/txw1314.github.io.git`  )

填好后在`Git Bash`中输入下列命令部署到`Gitee`仓库

在仓库的服务`-Gitee Pages`进行手动部署

`Github Pages`会自动使用你仓库的代码进行部署，而`Gitee`需要你手动更新,详细百度参考

等待部署结束后，访问`Https://Gitee用户名.gitee.io`查看部署结果

## 3.3 部署到Vercel
请在看过3.1部署到`Github`后再观看本部分教程,此处不做介绍。


本篇文章基本讲述了Hexo博客的基本部署，包括了本地化部署测试和上传到Github，Gitee等平台，使用托管平台提供的Page服务进行远程访问。

本篇教程属于面向与小白的零基础教程系列，如果在安装过程中出现任何问题，你可以在评论区提问，你的提问也是我充实文章的助力！

关注上杉九月，关注上杉九月谢谢喵！

Hexo_01-博客的安装与部署
https://blog.sakurasep.site/posts/hexo01/
