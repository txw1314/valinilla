---
title: PicGo+typora上传图片失败报422的原因及解决方法
tags: PicGo
categories: PicGo
description: PicGo+typora上传图片失败报422的原因及解决方法
comments: true
top: false
pin: false
music:
  server: netease
  type: song
  id: 1421191783
date: 2022-08-03 17:31:35
updated: 2022-08-03 17:31:35
index_img: https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208021030428.jpg
banner_img: https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208021030428.jpg
headimg: https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208021030428.jpg
img: https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208021030428.jpg
cover: https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208021030428.jpg
sticky:
---

picgo 用 github 作图床，使用 typora 上传图，出现 StatusCodeError: 422 的原因及解决方法

### 我在使用过程中 PicGo 出现了 StatusCodeError: 422 的错误，上传图片失败。通过百度得知是以下原因造成的

> **PicGo 目前不支持在 gitbub 上上传同名文件，上传同名文件就会报错，即使是两张不同的图片。**

解决方式也很简单，Picgo 开启上传时重命名和时间戳重命名就可以结局，或者把 github 里面已经有的同名文件删除，都可以解决这个问题。
