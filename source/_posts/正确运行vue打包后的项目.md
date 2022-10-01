---
title: 正确运行vue打包后的项目
author: 作者
tags: 
  - vue
  - webpack
categories: 
  - 前端
  - vue
description: 怎么使用webpack打包后的vue项目正确运行
comments: true
music:
  server: netease
  type: song
  id: 1916550868
date: 2022-08-08 22:54:51
updated: 2022-08-08 22:54:51
index_img: https://pic.3gbizhi.com/2021/1228/thumb_1680_0_20211228074310530.jpg
banner_img: https://pic.3gbizhi.com/2021/1228/thumb_1680_0_20211228074310530.jpg
headimg: https://pic.3gbizhi.com/2021/1228/thumb_1680_0_20211228074310530.jpg
img: https://pic.3gbizhi.com/2021/1228/thumb_1680_0_20211228074310530.jpg
cover: https://pic.3gbizhi.com/2021/1228/thumb_1680_0_20211228074310530.jpg
---

这篇文章给大家分享的是有关怎么使用webpack打包后的vue项目正确运行的内容。小编觉得挺实用的，因此分享给大家做个参考，一起跟随小编过来看看吧。

　　我们知道使用webpack打包vue项目后会生成一个dist文件夹，dist文件夹下有html文件和其他css、js以及图片等，那么打包后的文件该如何正确运行呢？

　　倘若直接打开html文件，会报如下错误：　　

　　那么该如何运行呢？其实可以将生成的dist文件部署到express[服务器](https://www.yisu.com/)上运行。

##　　（1）、安装express-generator生成器。　　　　

```
npm install express-generator -g // 也可使用cnpm比较快　
```

##　　（2）、创建一个express项目。

```
express expressName // expressName是项目名
```

##　　（3）、进入项目目录，安装相关项目依赖。　　

```
cd expressName
npm install // 或cnpm install
```

##　　（4）、此时生成的项目目录应该是这样的：

　　　![image-20220808225834865](https://gcore.jsdelivr.net/gh/txw1314/blog-img@main/img/202208090007353.png)

## （5）、将dist文件夹下的所有文件复制到express项目的publick文件夹下面，然后运行npm start来启动express项目。

## （6）、打开浏览器，输入localhost:3000就可以看到效果了。例如我的是这样的：　

　　　　![image-20220808225854668](https://gcore.jsdelivr.net/gh/txw1314/blog-img@main/img/202208090007996.png)

感谢各位的阅读！关于“怎么使用webpack打包后的vue项目正确运行”这篇文章就分享到这里了，希望以上内容可以对大家有一定的帮助，让大家可以学到更多知识，如果觉得文章不错，可以把它分享出去让更多的人看到吧！
