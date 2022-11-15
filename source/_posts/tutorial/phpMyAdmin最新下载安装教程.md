---
title: phpMyAdmin最新下载安装教程
author: 作者
tags: phpMyAdmin
categories:
  - 破解软件
description: phpMyAdmin最新下载安装教程
comments: true
music:
  server: netease
  type: song
  id: 1916550868
date: 2022-08-08 22:26:31
updated: 2022-08-08 22:26:31
index_img: https://pic.3gbizhi.com/2019/1120/thumb_1680_0_20191120092758388.jpg
banner_img: https://pic.3gbizhi.com/2019/1120/thumb_1680_0_20191120092758388.jpg
headimg: https://pic.3gbizhi.com/2019/1120/thumb_1680_0_20191120092758388.jpg
img: https://pic.3gbizhi.com/2019/1120/thumb_1680_0_20191120092758388.jpg
cover: https://pic.3gbizhi.com/2019/1120/thumb_1680_0_20191120092758388.jpg
---

本篇文章主要为大家详细地介绍了**PHPmyadmin 安装教程**。

PHPmyadmin 是我们在日常项目开发中常用的 MySQL 数据库管理器之一！那么如何快速下载安装好 PHPmyadmin 就是新手朋友们不可或缺的一项技能了，掌握了这个技能后无论你是需要重新搭建开发环境还是后期误删 PHPmyadmin，这些问题都能轻松解决。

下面我们结合具体的图文信息为大家详细地介绍如何**下载安装 PHPmyadmin**以及**PHPmyadmin 怎么登陆启动**的方法！

## **一、下载 PHPmyadmin**

打开 PHP 中文网中的 PHPmyadmin 工具下载链接：http://www.php.cn/xiazai/gongju/97，

点击本地下载，即可下载 PHPmyadmin 压缩包。

## **二、更改文件夹名及部分代码**

当我们下载了 PHPmyadmin 文件的压缩包后，将其解压到 c 盘的根目录下。并且把原先的文件夹名称改为 PHPmyadmin。

![056a3d7632a8705ec09729b4d35c534.png](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208090005749.png)

然后打开这个文件夹，找到 config.sample.inc.php，将其重命名为 config.inc.php。

![cd60a47f5de42a9edf47c8f4e73dd8f.png](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208090005315.png)

最后打开 config.inc.php 文件，找到这段代码：

```
$cfg['blowfish_secret'] = ''
```

将其改为下面这么这段代码：

```
$cfg['blowfish_secret'] = 'c4ca4238a0b923820dcc509a6f75849b';//一个长字符串密码就行
```

保存退出即可。

## **三、**新建一个 phpmyadmin.conf 文件

首先我们要找到 PHP 环境中的 Apache 的 conf 文件夹，在里面直接新建一个 phpmyadmin.conf 文件。例如在 PHPstudy 环境下，conf 文件夹所在位置如下图：

![b066f5c3fd472af38dd1c2b65e0ad1d.png](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208090005122.png)

然后在这个新建的文件里，直接复制粘贴这段代码：

```
Alias /phpmyadmin "c:/phpMyAdmin/"
<Directory "c:/phpMyAdmin/">
Options Indexes FollowSymLinks MultiViews
AllowOverride all
Require all granted
php_admin_value upload_max_filesize 128M
php_admin_value post_max_size 128M
php_admin_value max_execution_time 360
php_admin_value max_input_time 360
</Directory>
```

最后保存退出即可。

## **四、修改配置文件 httpd.conf**

在 Apache 的 conf 文件夹里找到 httpd.conf 文件，打开文件，在文本末尾处加上这一段代码：

```
Include conf/phpmyadmin.conf
```

![1c992fa891b68dd4aba763962da5b56.png](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208090005005.png)

最后重启 Apache 即可。

## **五、登录启动 PHPmyadmin**

经过上述四步后，就已经成功安装好了 PHPmyadmin，**那怎样登录 PHPmyadmin？**此时就可以访问这个链接地址：localhost/phpmyadmin，或者 127.0.0.1/phpmuadmin。**注：链接里的 phpmyadmin 需小写。**

![899675ce0dd44af512bb0763fc4c629.png](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208090005989.png)

出现了 PHPmyadmin 登录界面：

![827af5e216d26209744a042f4522924.png](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208090005543.png)

一般初始的用户名密码都是 root，点击执行即可成功登陆启动 PHPmyadmin 的管理界面，如下图：

![1536550810326318.png](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208090006977.png)

那么以上文章就是关于 PHPmyadmin 下载安装的具体过程介绍，希望对有需要的朋友有所帮助！

各位也可以参考对应的视频教程【[下载安装以及配置线上数据库管理工具 PHPMyAdmin](http://www.php.cn/code/28299.html)】，此视频解说更加直观、浅显易懂！

文章来源于：https://www.php.cn/jishu/mysql/409664.html
