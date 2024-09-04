---
title: 正确运行vue打包后的项目
author: 作者
tags:
  - vue
  - webpack
categories:
  - 前端
description: 怎么使用webpack打包后的vue项目正确运行
comments: true
music:
  server: netease
  type: song
  id: 1916550868
date: 2022-08-08 22:54:51
updated: 2022-08-08 22:54:51
index_img: https://pic.qqans.com/up/2024-6/17182507949401213.jpg
banner_img: https://pic.qqans.com/up/2024-6/17182507949401213.jpg
headimg: https://pic.qqans.com/up/2024-6/17182507949401213.jpg
img: https://pic.qqans.com/up/2024-6/17182507949401213.jpg
cover: https://pic.qqans.com/up/2024-6/17182507949401213.jpg
---

这篇文章给大家分享的是有关怎么使用 webpack 打包后的 vue 项目正确运行的内容。小编觉得挺实用的，因此分享给大家做个参考，一起跟随小编过来看看吧。

我们知道使用 webpack 打包 vue 项目后会生成一个 dist 文件夹，dist 文件夹下有 html 文件和其他 css、js 以及图片等，那么打包后的文件该如何正确运行呢？

倘若直接打开 html 文件，会报如下错误：

那么该如何运行呢？其实可以将生成的 dist 文件部署到 express[服务器](https://www.yisu.com/)上运行。

##　　（1）、安装 express-generator 生成器。

```
npm install express-generator -g // 也可使用cnpm比较快　
```

##　　（2）、创建一个 express 项目。

```
express expressName // expressName是项目名
```

##　　（3）、进入项目目录，安装相关项目依赖。

```
cd expressName
npm install // 或cnpm install
```

##　　（4）、此时生成的项目目录应该是这样的：

![怎么使用webpack打包后的vue项目正确运行](https://cache.yisu.com/upload/information/20200622/114/33952.png)

## （5）、将 dist 文件夹下的所有文件复制到 express 项目的 publick 文件夹下面，然后运行 npm start 来启动 express 项目。

## （6）、打开浏览器，输入 localhost:3000 就可以看到效果了。例如我的是这样的：　

![怎么使用webpack打包后的vue项目正确运行](https://cache.yisu.com/upload/information/20200622/114/33954.png)感谢各位的阅读！关于“怎么使用 webpack 打包后的 vue 项目正确运行”这篇文章就分享到这里了，希望以上内容可以对大家有一定的帮助，让大家可以学到更多知识，如果觉得文章不错，可以把它分享出去让更多的人看到吧！
