---
title: 使用github建立图床,picgo和typora上传图片
tags: 
  - github
  - picgo
  - typora
categories: github
type: categories
description: 建立图床必须具备什么条件   
  - 一个github账号
  - 一个公开的仓库
  - PicGo 上传图片
  - Typora 上传图片
date: 2022-07-29 17:26:52
---
建立图床必须具备什么条件 

>首先你需要一个github账号，如果没有的话，请先注册。<br/>
>github官网地址 [github.com](https://github.com/) 
>PicGo下载地址 [PicGo](https://molunerfinn.com/PicGo/)  
  - 一个github账号
  - 一个公开的仓库
  - PicGo 上传图片
  - Typora 上传图片

# 一、新建仓库

## 1.1 创建一个新仓库，用于存放图片。

填写仓库名称和描述，且仓库必须是public的，否则存储的图片不能正常访问。![新建仓库](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/200.png)

## 1.2 生成一个token，用于picGo访问github

选择左侧菜单的Developer settings

之后选择左侧Personal access tokens，再点击Generate new token
![生产token的位置](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/204.png)

填写Note，勾选repo.
![](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/205.png)
注意，生成的token只会在这里显示一次，所以记得单独保存下来哦。
![](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/206.png)
至此，Github的配置完成。

# 二、下载picGo，并进行配置

## 2.1 下载

访问picGo下载地址，选择 picGo-Setup-XXX.exe下载软件安装包即可。

如果安装成功，picGo不能正常使用，则可以用兼容模式启动,或者重启电脑。【此问题因电脑而异,重启电脑能解决百分之九十九的问题。】

## 2.2 配置

仓库名：[github用户名]/[第一步新建的仓库名称]

分支：默认master，从2020.10.01开始，github的默认分支名变更为main

设定token：第一步创建的token

指定存储路径：可填可不填，如果填写了，图片就会存储在img文件夹下

设定自定义域名： `https://cdn.jsdelivr.net/gh/[github用户名]/[仓库名]@main`,注意，此处的分支一定要填写@main，否则默认使用master分支。而现在github创建的默认分支名为main，如果不指定，则会出现图片不能上传的情况。我的是: ` https://cdn.jsdelivr.net/gh/txw1314/blog-img@main `
![配置picGo](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/207.png)

## 2.3 插件安装

点击插件设置右边的图标，进入插件网页，选择表格中的插件名称复制到input输入框,选择插件安装，可显示更多内容
![安装插件](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/208.png)

至此，github+picGo的配置完成，可以在上传区进行图片上传了。

补充几点

>1. 原本github的自定义域名应该是： ` https://raw.githubusercontent.com/[username]/[仓库名] `
但是使用这种方式访问图片巨慢，所以建议使用jsdelivr作为cdn加速。改变域名即可，不需要任何其他配置。` https://cdn.jsdelivr.net/gh/txw1314/blog-img@main `

>2. 配置完成，可能出现不能上传的情况，请大家耐心检查，也许某一步的配置出现了问题，实在不行就重启电脑，毕竟重启电脑能解决99%的问题。

>3. 不止可以用github作为图床，还可以使用国内的码云(gitee)。当然也有收费的七牛、阿里云等等。在安装插件之后会有诸多选项。

# 三、上传图片

上面配置完成，下面我们就可以上传图片了。

## 3.1 上传图片

![上传图片](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220730230508076.png)

## 3.2 上传图片完成

![上传图片完成](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220730230548376.png)

picGo监听端口设置

选择“PicGo设置”–>“设置server”


>如果监听端口不是36677，则需要修改为36677。否则会出现picGo能正常上传 图片，而typora上传图片失败的情况。
>如果picGO不能正常上传图片，建议重启电脑，我就是重启了之后就能正常上传图片了，只是图片不会显示缩略图

# 四 、使用Typora上传图片

## 4.1 点击Typora文件—偏好设置

如下图所示，选择图像，勾选右侧选项，上传服务，选择picgo路径，即可配置完成

![image-20220730231031969](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220730231031969.png)

## 4.2 我们也可以点击验证图片上传选项试一下

![image-20220730231355986](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220730231355986.png)

## 4.3 验证成功

![image-20220730232927677](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220730232927677.png)

## 4.4 我的验证失败了，虽然失败了，但是不影响我上传图片，嗯，问题不大，哈哈哈

![image-20220730231402492](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220730231402492.png)



然后就是在Typora复制文件图片，右键上传图片，稍等一下就会自动完成

> tip: 在Typora粘贴图片的时候，个人建议使用Snipaste这个软件，非常方便！
