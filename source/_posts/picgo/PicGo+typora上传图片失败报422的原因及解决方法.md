---
title: PicGo+typora上传图片失败报422的原因及解决方法
author: vanilla
tags: PicGo
categories: PicGo
description: PicGo+typora上传图片失败报422的原因及解决方法
comments: true
top: false
pin: false
music:
  server: netease
  type: song
  id: 1916550868
date: 2022-08-03 17:31:35
updated: 2022-08-03 17:31:35
index_img: https://raw.githubusercontent.com/txw1314/blog-img/main/img/202208021030428.jpg
banner_img: https://raw.githubusercontent.com/txw1314/blog-img/main/img/202208021030428.jpg
headimg: https://raw.githubusercontent.com/txw1314/blog-img/main/img/202208021030428.jpg
img: https://raw.githubusercontent.com/txw1314/blog-img/main/img/202208021030428.jpg
cover: https://raw.githubusercontent.com/txw1314/blog-img/main/img/202208021030428.jpg
sticky:
---

picgo用github作图床，使用typora上传图，出现StatusCodeError: 422 的原因及解决方法

###  我在使用过程中PicGo出现了StatusCodeError: 422 的错误，上传图片失败。通过百度得知是以下原因造成的

> **PicGo目前不支持在gitbub上上传同名文件，上传同名文件就会报错，即使是两张不同的图片。**

解决方式也很简单，Picgo开启上传时重命名和时间戳重命名就可以结局，或者把github里面已经有的同名文件删除，都可以解决这个问题。
