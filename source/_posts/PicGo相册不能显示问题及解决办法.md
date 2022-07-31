---
title: PicGo相册不能显示问题及解决办法
tags: PicGo
categories: PicGo
type: categories
description: PicGo相册不能显示问题及解决办法
date: 2022-07-30 22:30:02
---

我的PicGo图片上传成功了，但是相册区域图片不能正常显示，如下图所示

![](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/209.png)

## 解决办法

### 1.0 重启应用

退出应用，重新启动，上传的图片能正常显示

### 2.0 卸载应用，重新安装

卸载重装 PicGo，不需要重新配置，之后上传的图片都能正常显示

### 3.0 打开picgo设置，找到设置Server，把端口号修改成36677

![](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220730224030434.png)

![](https://cdn.jsdelivr.net/gh/txw1314/blog-img@main/img/image-20220730224111600.png)

### 4.0 修改host文件

> 原因是github屏蔽掉了图片，结局办法就是修改host，我就是用的这个方法解决的

host路径：

```
C:\Windows\System32\drivers\etc\hosts
```

找到host文件，用记事本格式打开，添加代码

```# GitHub Start 
140.82.113.3      github.com
140.82.114.20     gist.github.com
151.101.184.133    assets-cdn.github.com
151.101.184.133    raw.githubusercontent.com
151.101.184.133    gist.githubusercontent.com
151.101.184.133    cloud.githubusercontent.com
151.101.184.133    camo.githubusercontent.com
151.101.184.133    avatars0.githubusercontent.com
199.232.68.133     avatars0.githubusercontent.com
199.232.28.133     avatars1.githubusercontent.com
151.101.184.133    avatars1.githubusercontent.com
151.101.184.133    avatars2.githubusercontent.com
199.232.28.133     avatars2.githubusercontent.com
151.101.184.133    avatars3.githubusercontent.com
199.232.68.133     avatars3.githubusercontent.com
151.101.184.133    avatars4.githubusercontent.com
199.232.68.133     avatars4.githubusercontent.com
151.101.184.133    avatars5.githubusercontent.com
199.232.68.133     avatars5.githubusercontent.com
151.101.184.133    avatars6.githubusercontent.com
199.232.68.133     avatars6.githubusercontent.com
151.101.184.133    avatars7.githubusercontent.com
199.232.68.133     avatars7.githubusercontent.com
151.101.184.133    avatars8.githubusercontent.com
199.232.68.133     avatars8.githubusercontent.com
# GitHub End
```

> tip: host文件修改需要管理员权限，可在桌面复制一份，用修改完的文件替换掉原来的文件即可，权限可以自己更改，搞完再改回去
