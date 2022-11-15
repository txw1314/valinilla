---
title: hexo之评论系统——twikoo
author: 作者
tags:
  - 评论系统
  - twikoo
categories: Hexo系列
description: hexo之评论系统——twikoo
top: false
pin: false
comments: true
music:
  server: netease
  type: song
  id: 1960477667
date: 2022-08-02 13:07:14
updated: 2022-08-02 13:07:14
sticky:
## 文章头图设置
index_img: https://img1.baidu.com/it/u=674567296,600896811&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
banner_img: https://img1.baidu.com/it/u=674567296,600896811&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
headimg: https://img1.baidu.com/it/u=674567296,600896811&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
img: https://img1.baidu.com/it/u=674567296,600896811&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
cover: https://img1.baidu.com/it/u=674567296,600896811&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
---

# 写在前面

Hexo 博客里面支持的评论系统有：Disqus、Disqusjs、Livere、Gitalk、Valine、Waline、Utterances、Facebook Comments、Twikoo、Giscus，这里面有的评论有的是国外的服务器、有的有广告，本文要讲的 Twikoo 是在 butterfly3.3 之后支持的，它支持邮件提醒、微信提醒等功能，还是非常好用的。

> 注意：本文仅针对腾讯云的部署方式中的「手动部署」，其他详细部署方式请参考官方文档。

# 购买云开发套餐

## 温馨提示：如果你已经拥有云开发环境，可以忽略这一步，直接到【登录授权】。

### 1、进入云开发 CloudBase，进行登录、实名认证操作，点击控制台：

![image-20220802131130556](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333827.png)

### 2、点击云产品，选择云开发 CloudBase：

![image-20220802131147641](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333828.png)

### 3、点击新建，选择空模板，点击下一步：

![image-20220802131211301](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333829.png)

![image-20220802131229324](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333830.png)

### 4、选择合适的套餐进行购买：

![image-20220802131347628](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333831.png)

> 温馨提示：
> 地域选择【上海】
> 计费方式选择【包年包月】
> 环境名称自由填写
> 套餐版本选择【特惠基础版 1】,白嫖我选择免费版

### 5、按照上面的步骤操作之后，我们会拥有一个云开发环境：

![image-20220802131455040](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333832.png)

> 注意：记录一下这个环境 ID，我们后面会用。

登录授权
环境 - 登录授权 - 开启【匿名登录】

![image-20220802131558824](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333833.png)
安全配置
环境 - 安全配置 - 添加域名：将自己的域名添加进去

![image-20220802131716213](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333834.png)

> 温馨提示：
> 如果更改了域名发现评论加载不出来的情况，请记得回来更改为最新域名，尤其是那些刚开始使用 github.io 来作为自己博客域名的童鞋，哪天购买了自己的域名，记得换，记得换，记得换（重要的事情说三遍)。

# 云函数

### 1、环境 - 云函数 - 新建云函数

> 温馨提示：
> 函数名称填写：twikoo
> 创建方式选择：空白函数
> 运行环境选择：Nodejs10.15
> 函数内存选择：128M
> 必须按照上面的方式选择，不要瞎选瞎写好吧。

![image-20220802131857735](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333835.png)

![image-20220802131825047](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333836.png)

![image-20220802131924094](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333837.png)

### 2、清空上图中「函数代码」框里的内容，复制`exports.main = require('twikoo-func').main`到里面，点击确定，如下：![image-20220802132003674](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333838.png)

### 3、点击「twikoo」函数名进入云函数详情页 - 函数代码 - 文件 - 新建文件，输入 package.json 确定，将`{ "dependencies": { "twikoo-func": "1.5.11" } }`内容复制到新建的文件`package.json`里面。

![image-20220802132113490](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333839.png)

![image-20220802132131683](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333840.png)

# 配置 butterfly 主题文件

打开`主题Volantis`下的配置文件

```
comments:
  title: <i class='fa-solid fa-comments'></i> 评论
  subtitle:
  service: twikoo #giscus
  # 可选评论系统 # twikoo giscus(实现了，只是嫌弃样式丑陋用了第一个)

  # Twikoo 有限使用这个，这个好看呀
  # https://twikoo.js.org/
  twikoo:
    js: https://unpkg.com/twikoo@latest # 建议锁定版本
    path: window.location.pathname # 全局评论地址
    # 其他配置项按照yml格式继续填写即可 除了 [el path] 选项
    envId: vanilla-yiyi-6gxfhkqy46f064ce # 腾讯云环境id 这里我做了改写，这个是不真实的
    placeholder: #全局评论占位，也可以在管理面板中的配置管理处设置（此处优先级更高）

```

显示效果如下：

![image-20220802132912374](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/douyin/202208021333841.png)

# 最后

关于 Twikoo 评论系统详细文档请参考：Twikoo 官方文档（https://twikoo.js.org）
文章来源于网络：

> 作者：重庆妹子在霾都
> 链接：https://www.jianshu.com/p/c00b8e329f46
> 来源：简书
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
