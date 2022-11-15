---
title: 如何在Windows下搭建WordPress博客站点
author: 作者
tags: WordPress
categories: 博客
description: 如何在Windows下搭建WordPress博客站点
comments: true
music:
  server: netease
  type: song
  id: 1916550868
date: 2022-10-30 19:52:28
updated: 2022-10-30 19:52:28
index_img: https://t7.baidu.com/it/u=1032479594,2383177859&fm=193&f=GIF
banner_img: https://t7.baidu.com/it/u=1032479594,2383177859&fm=193&f=GIF
headimg: https://t7.baidu.com/it/u=1032479594,2383177859&fm=193&f=GIF
img: https://t7.baidu.com/it/u=1032479594,2383177859&fm=193&f=GIF
cover: https://t7.baidu.com/it/u=1032479594,2383177859&fm=193&f=GIF
---

[TOC]

## 概述

本教程是《Windows下如何使用cpolar搭建Web站点系列》第4篇，前面已经介绍cpolar的安装，搭建了一个简单的演示站点，并且配置好了开机自启动。如果您没看过之前的教程，请先阅读[《第一篇》](https://juejin.cn/post/7072273383966113800)。

本篇继续，搭建一个真正有用的Web站点，您可以用它来撰写博客、搭建您自己的企业站点，外贸站点等，并且发布至公网上。

## 前置准备

查看当前WordPress版本的组件依赖需求

访问WordPress官网: [wordpress.org/download/](https://link.juejin.cn?target=https%3A%2F%2Flink.zhihu.com%2F%3Ftarget%3Dhttps%3A%2F%2Fwordpress.org%2Fdownload%2F)

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0e8221e0b292488f8f4bf8eb7489b871~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

在本教程发布时，当前最新的WordPress版本为5.8.2

下面红框位置显示，它需要依赖PHP 7.4

我们对比一下PHPStudy里的组件版本，当前PHP 7.4没有安装，后面需要安装一下。其它的我们都已经满足。

接下来，我们要做如下操作：

- 安装数据库管理工具
- 创建一个数据库
- 安装PHP 7.4
- 为WordPress新创建一个站点
- 安装与配置WordPress

## 1 安装数据库管理工具

### 1.1 安装图形图数据库管理工具，SQL_Front

在PHPStudy面板-`软件管理`-找到SQL_Front，点击`安装`按钮

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2e6da1b5d7c741cc8c5ece10dfc6ac78~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

安装后，点击`管理`按钮，打开数据库工具

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3adb659b21fb4492aa20efd78b59d910~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

选择`localhost`本地数据库，点击`打开`按钮

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5605a4ebfce4463f95940bfaa6e79fdc~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

如有错误提示，点击`确认`，忽略即可,不影响。

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/10c8f3d27b864312a145582ca7fa6255~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

## 2 创建一个新数据库

### 2.1 创建数据库

在localhost上点击右键，选择`新建`--`数据库`

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/70639f23b3d742ecaa8dc11b0b644aff~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

数据库名称，可以自定义,这里填写如下：

数据库名称: `wordpress` 字符集: `utf8mb4` 字符集校队: `utf8mb4_unicode_ci`

之后，点击`确认`按钮。

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/38e12b507a8642b3a04268a9a662fab8~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/399929e060cd4daca6a28ddeebd3da02~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

数据库创建成功。

### 2.2 为数据库创建一个用户

为了安全起见，我们为wordpress数据库，单独创建一个的用户名和密码，用于管理它，而不是使用root账号。

在`用户`点击右键，弹出菜单，选择 `新建`--`用户`

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f17ced89a24a4eda806d86eda95c6e96~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

本例中，我们创建一个简单用户名user1，密码:12345678

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4305b4901a1041bc9fdccd3e181b8012~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

> 注：本例是为了教学演示，用户名及密码简单，您在生产环境，应该创建更复杂的用户名和密码。

选择`权限`栏，为用户添加权限，在`赋予权限`选择数据库，并指定wordpress数据库，然后在右侧勾选所有权限。该用户只能控制wordpress数据库，而不能读写其它数据库。

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4692d9e7d59d41a08783beca1fe717f4~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

选择配置好的wordpress权限，点击`确定`按钮。

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c3d68814fa6a4d47bf75965311cde990~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

添加好以后，如下图所示：

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/fc11acec1a514f99ac88732291563b2e~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

## 3 安装PHP7.4

在PHPStudy管理面板--`软件管理`-- php7.4.3nts，点击`安装`。

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5172c66530514bde9f9ea9251e4052aa~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

## 4. 创建一个新站点

### 4.1 创建站点根目录

我们在D盘，创建一个websites目录，再在下面创建一个site1目录，作为本次wordpress站点的根目录，如图：

### 4.2 访问WordPress官网，下载最新版本的压缩包

下载地址: [wordpress.org/latest.zip](https://link.juejin.cn?target=https%3A%2F%2Flink.zhihu.com%2F%3Ftarget%3Dhttps%3A%2F%2Fwordpress.org%2Flatest.zip)

下载后解压，将所有文件内容，复制

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9f4254182c7b4c7e9a674f9fde99de07~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

粘贴到site1目录下，如下图：

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/299d202702374c6dbd9da2baf9c581e7~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

### 4.3 创建新Web站点

在PHPStudy面板--网站--点击`创建网站`按钮

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c01f7059d493466ea31e88fa6a6e3bf0~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

按下图配置：

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/dc26ab860b594005b9c7e5e9d592ac45~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

我们在本机，8080端口上，创建了一个新站点。如下图：

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/710f2c6a2b8745bc9bab5f1783bb85b5~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

### 4.4 打开浏览器测试一下

[http://localhost:8080/](https://link.juejin.cn?target=https%3A%2F%2Flink.zhihu.com%2F%3Ftarget%3Dhttp%3A%2F%2Flocalhost%3A8080%2F) ,显示如下图，证明新网站创建成功。

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7c2cef6861ea46cfb1eaa61bba0a9b08~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

## 5 cpolar配置

如果之前没有安装过cpolar，请参考这个系列的[《第一篇》](https://link.juejin.cn?target=https%3A%2F%2Fzhuanlan.zhihu.com%2Fp%2F430753222)教程。

### 5.1 在后台预留一个二级子域名

[cpolar后台](https://link.juejin.cn?target=https%3A%2F%2Flink.zhihu.com%2F%3Ftarget%3Dhttps%3A%2F%2Fdashboard.cpolar.com%2F)--预留--保留二级子域名，本例中: 二级子域名: dev10 (您可以配置成不同的) 地区: 选择 `China VIP`（cn_vip） 描述: wordpress （可选）

如下图：

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a5cb7f5b42604b9e8c03319e7840ddb2~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

### 5.2 修改cpolar配置文件，添加一个隧道指向8080端口

使用VS Code，打开cpolar配置文件

本例中,配置文件的路径在：C:\Users\michael.cpolar\cpolar.yml

打开后的样式：

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9aa727e5c02c4a049f85b0f38eccacae~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

我们在配置文件的最后面，添加一个新的隧道 隧道名称为wordpress,指向8080端口，二级子域名为dev10，地区是cn_vip，如下：

```yaml
wordpress:
    proto: http
    addr: "8080"
    subdomain: dev10  #这里改为您自己的二级子域名
    region: cn_vip
复制代码
```

修改后的配置文件，如下图：

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f920de4e4b2e4ba58a0654d2ac659502~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

> 注意：ymal格式是缩进敏感的，注意wordpress隧道的缩进与上面演示站点website的缩进是一致的。

如果缩进不一致，请适当调整。

修改后，保存文件。

### 5.3 验证cpolar配置文件是否正确

以管理员方式打开命令行窗口

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/02c74ca8f7274738889a96c1a1bf272c~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

关掉后台的cpolar服务

```arduino
cpolar service stop
复制代码
```

在前台运行cpolar，子命令使用start-all，意思是启动配置文件所有隧道，以测试配置文件是否正确。

```sql
cpolar start-all
复制代码
```

如显示下图，则说明配置文件正确。

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2901d600a05a4cf59ad130af770ee8c6~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

按CTRL+C，关掉前台cpolar

启动后台cpolar服务

```sql
cpolar service start
复制代码
```

我们打开浏览器，测试一下 [dev10.vip.cpolar.cn/](https://link.juejin.cn?target=https%3A%2F%2Flink.zhihu.com%2F%3Ftarget%3Dhttp%3A%2F%2Fdev10.vip.cpolar.cn%2F)

如同样显示下图，则说明公网域名配置成功了。

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/32e0d9f10a8f4d30b458228774caa85d~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

### 6 WordPress初始化配置

### 6.1 WordPress初始化设置

现在开始进行WordPress初始化设置

选择`中文简体`，按`继续`按钮

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5bfe561c928f4fe194e277a0c6f0bb3a~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

这里使用前面创建的数据库账号和密码

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d87401bd0bdb437a894d43da4dd88c54~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a4d67d2c305a4e9284c6319e0e9b4cf9~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

这里可以根据您的喜欢自定义配置，点击`安装WordPress`

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/63a4fd24fa97491ba3469c1fbbe1669a~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

安装成功后，跳转到Wordpress的后台控制面板

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d091fafe5ad548f88563fd281270d505~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

安装WordPress成功！

### 6.2 为WordPress定制主题

WordPress是非常可定制的。通过在页面顶部的 WordPress 横幅中单击您的站点名称（当您登录时），您将被带到仪表板。从那里，您可以更改主题、添加页面和帖子、编辑菜单、添加插件等等。这只是在 Raspberry Pi 的 Web 服务器上设置一些有趣的东西的品尝器。

下面，我们更换一个主题试试。

WordPress仪表盘-->`外观`-->`主题`

点击`安装主题`按钮，如下图：

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0d727dba2b4e4eda99c3ba6c4c26bde6~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

点击`热门`，选择一个自己喜欢的主题，点击`安装`按钮

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b12a2ffce47f4cea86412a405937715e~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

主题安装成功后，点击`启用`按钮。

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/93d6ef35138142b88c3d0cc600b63f93~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

新开一个浏览器窗口，打开 [dev10.vip.cpolar.cn/](https://link.juejin.cn?target=https%3A%2F%2Flink.zhihu.com%2F%3Ftarget%3Dhttp%3A%2F%2Fdev10.vip.cpolar.cn%2F)

我们来浏览一下新主题的效果。

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/94e1558a3a6d435d93b9e0e772a48ef7~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

恭喜！我们的新博客站点，已经基本创建成功了！

### 6.4 安装WordPress相对URL插件（必需）

您必须确保WordPress发布为相对URL，否则使用https地址访问时将出现错误。

您可以通过安装以下插件之一来完成此操作

插件：

- [odt-relative-urls](https://link.juejin.cn?target=https%3A%2F%2Flink.zhihu.com%2F%3Ftarget%3Dhttps%3A%2F%2Fgithub.com%2Foptimizamx%2Fodt-relative-urls)
- [relative-url](https://link.juejin.cn?target=https%3A%2F%2Flink.zhihu.com%2F%3Ftarget%3Dhttp%3A%2F%2Fwordpress.org%2Fplugins%2Frelative-url%2F)
- [root-relative-urls](https://link.juejin.cn?target=https%3A%2F%2Flink.zhihu.com%2F%3Ftarget%3Dhttp%3A%2F%2Fwordpress.org%2Fplugins%2Froot-relative-urls%2F)

本例中，我们安装`Relative URL`插件：

- 登录WordPress`仪表盘`-->`插件`-->`安装插件`

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7e98c77839044280b42707f68fb0dd33~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

- 在关键词搜索栏输入`Relative URL` 回车

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/80c34a8c8b80477a86b48421ef753e7d~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

- 找到插件后点击`现在安装`按钮
- 当安装成功后，点击`启用`按钮，激活插件。

### 修改config.php配置

您必须确保Wordpress了解它是为了通过隧道主机名提供服务。 您可以通过修改wp-config.php来配置Wordpress以包含以下行：

```bash
define('WP_SITEURL', 'http://' . $_SERVER['HTTP_HOST']);
define('WP_HOME', 'http://' . $_SERVER['HTTP_HOST']);
复制代码
```

- 修改wp-config.php文件 打开网站根目录下的wp-config.php文件，添加上面的项，然后保存。

配置好以后如图：

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9d9c69deb6494fdeb907115da02d78cf~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

现在，我们的博客站点可以被公网正常访问啦！让我们看看效果：

使用https地址访问: [dev10.vip.cpolar.cn/](https://link.juejin.cn?target=https%3A%2F%2Flink.zhihu.com%2F%3Ftarget%3Dhttps%3A%2F%2Fdev10.vip.cpolar.cn%2F)

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5f698138768b44d2805c4957d62a230b~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp)

看着红框里美丽的小锁头，现在心情好多了。^ ^

我们已经成功搭建起了WordPress站点。

## 总结：

我们创建了一个新Web站点，安装配置了wordpress最新版本，并且配置了公网隧道，二级子域名，并且给新站点配置了主题样式，您拥有了一个属于自己的博客站点，可以写博客，开启自己的自媒体之旅。

在后面的教程里，我们会继续完善WordPress站点的配置，为其配置SSL，如果您喜欢，请分享给好友，并且关注后续章节。

**欢迎进一步了解更多关于cpolar的讯息~**


链接：https://juejin.cn/post/7072560430949859364
来源：稀土掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
