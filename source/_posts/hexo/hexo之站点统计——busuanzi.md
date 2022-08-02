---
title: hexo之站点统计——busuanzi
author: 作者
tags: 
  - busuanzi
  - 站点统计
categories: Hexo系列
description: 站点信息之busuanzi，及其相关配置信息的获取
top: false
pin: false
comments: true
music:
  server: netease
  type: song
  id: 1396930668
date: 2022-08-01 22:32:56
updated: 2022-08-01 22:32:56
sticky:
## 文章头图设置
index_img: https://img0.baidu.com/it/u=3440708810,3442918705&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
banner_img: https://img0.baidu.com/it/u=3440708810,3442918705&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
headimg: https://img0.baidu.com/it/u=3440708810,3442918705&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
img: https://img0.baidu.com/it/u=3440708810,3442918705&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
cover: https://img0.baidu.com/it/u=3440708810,3442918705&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
---
本片介绍的是站点信息统计之busuanzi
# 一、站点信息
## 1.1 在_config.volantis.yml搜索`统计`,显示有站点统计信息
```
visitcounter: # 站点统计访客开启入口在下面⬇
      siteuv:
        enable: true
        text: '本站访客数：'
        unit: '人'
      sitepv:
        enable: true
        text: '本站总访问量：'
        unit: '次'
```
## 1.2 接下来就是analytics引入busuanzi,这里就需要配置个人的app_id和app_key
```
# 站点统计访客开启入口，引入busuanzi，并配置属于自己的app_id和app_key
analytics:
  busuanzi: volantis-static/libs/busuanzi/js/busuanzi.pure.mini.js 
  leancloud: # 请使用自己的 id & key 以防止数据丢失
    app_id: u9j57bwJod4EDmXWdxrwuqQT-MdYXbMMI
    app_key: jfHtEKVE24j0IVCGHbvuFClp
    custom_api_server: # 国际版一般不需要写，除非自定义了 API Server
```
# 二、获取busuanzi的配置信息
## 2.1 打开leancloud官网，注册账号，该认证认证
>leancloud官网:https://www.leancloud.cn/ ,点击免费使用，注册账号

![注册账号](https://gcore.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220801224259281.png)
## 2.2 登录账号注册应用

![注册应用](https://gcore.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220801224618543.png)
## 2.3 点击应用，选择应用

![选择应用](https://gcore.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220801224734317.png)

## 2.4 点击设置，应用凭证，右侧就是我们想要的配置信息了

> 复制保存我们的配置信息，填入指定位置，页面就是有相关信息展示了

![获取配置信息](https://gcore.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220801225041384.png)

# 效果展示

> tip: 本地运行显示数据有点夸张了，还有点延迟，但是部署之后会显示正常数据

![本地运行](https://gcore.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220801230651942.png)

![部署之后](https://gcore.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220801225311587.png)
