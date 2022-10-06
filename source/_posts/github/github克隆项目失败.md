---
title: github克隆项目失败
tags: github
categories: github
description: github克隆项目失败,大概意思是：Fisheye/Crucible服务器不能识别git的SSL证书，所以操作停止执行,解决方法是...
type: categories
date: 2022-07-29 19:00:25
## 文章头图设置
index_img: https://img2.baidu.com/it/u=1830973642,518401107&fm=253&fmt=auto&app=120&f=JPEG?w=889&h=500
banner_img: https://img2.baidu.com/it/u=1830973642,518401107&fm=253&fmt=auto&app=120&f=JPEG?w=889&h=500
headimg: https://img2.baidu.com/it/u=1830973642,518401107&fm=253&fmt=auto&app=120&f=JPEG?w=889&h=500
img: https://img2.baidu.com/it/u=1830973642,518401107&fm=253&fmt=auto&app=120&f=JPEG?w=889&h=500
cover: https://img2.baidu.com/it/u=1830973642,518401107&fm=253&fmt=auto&app=120&f=JPEG?w=889&h=500
music: 
  server: netease
  type: song
  id: 557581095
---

## unable to access 'https://github.com/用户名/仓库名.git/': SSL certificate problem: self问题解决

## 前言

>今天想在github上找个项目玩玩，但是发现clone不下来，百度没有找到解决方案，于是又把git重装了一遍，发现还是不能clone,而且不能push，而且是同样的错误。于是Google了一下找到解决方案

## 原因
Git client in Fisheye/Crucible server perform verification on the SSL certificate and stop the process if it is unknown.

>大概意思是：Fisheye/Crucible服务器不能识别git的SSL证书，所以操作停止执行。

## 解决

  * 在git命令行输入以下命令即可

```
  git config --global http.sslVerify false
```