---
title: Win10自带软件卸载方法
author: 作者
date:  2022-10-15 01:40:33
updated:  2022-10-15 01:40:33
tags: 
categories: win10
description: Win10自带软件卸载方法
comments: true
music:
  server: netease
  type: song
  id: 1297802566
index_img: https://t7.baidu.com/it/u=737555197,308540855&fm=193&f=GIF
banner_img: https://t7.baidu.com/it/u=737555197,308540855&fm=193&f=GIF
headimg: https://t7.baidu.com/it/u=737555197,308540855&fm=193&f=GIF
img: https://t7.baidu.com/it/u=737555197,308540855&fm=193&f=GIF
cover: https://t7.baidu.com/it/u=737555197,308540855&fm=193&f=GIF
---

# Win10自带软件卸载方法【详细教程】

Win10自带软件怎么卸载 ?Win10一般都会在系统中预装不少软件，下面为大家带来了 Win10自带软件卸载教程 ，一起来看看。

　　使用命令卸载Win10内置软件

　　Win10系统内置的这些应用，可以通过“命令行”方式进行卸载的，支持卸载的应用以及对应的命令如下：

　　以管理员方式，打开 CMD 运行命名操作框，如，可以先按 Ctrl+X组合件，然后在搜索中，输入 CMD 然后在 命令提示符 中右键，点击以“管理员方式运行”，如下图所示。



　　打开命令运行窗口后，如果要卸载自带的 XBOX 应用，只要在命名窗口中，粘贴上命名 get-appxpackage *Microsoft.XboxApp* | remove-appxpackage 然后按下回车键(Enter)确认就可以了。

　　相关命令

　　闹钟时钟：get-appxpackage *Microsoft.WindowsAlarms* | remove-appxpackage

　　计算机：get-appxpackage *Microsoft.WindowsCalculator* | remove-appxpackage

　　相机：get-appxpackage *Microsoft.WindowsCamera* | remove-appxpackage

　　Groove音乐：get-appxpackage *Microsoft.ZuneMusic* | remove-appxpackage

　　邮件和日历：get-appxpackage *microsoft.windowscommunicationsapps* | remove-appxpackage

　　地图：get-appxpackage *Microsoft.WindowsMaps* | remove-appxpackage

　　电影和电视：get-appxpackage *Microsoft.ZuneVideo* | remove-appxpackage

　　Onenote：get-appxpackage *Microsoft.Office.OneNote* | remove-appxpackage

　　人脉：get-appxpackage *Microsoft.People* | remove-appxpackage

　　照片：get-appxpackage *Microsoft.Windows.Photos* | remove-appxpackage

　　语音录音机：get-appxpackage *Microsoft.WindowsSoundRecorder * | remove-appxpackage

　　XBOX：get-appxpackage *Microsoft.XboxApp* | remove-appxpackage



　　注意事项

　　这种方法，需要是管理员账户下运行。

　　以上就是我介绍的 Win10自带软件怎么卸载 Win10自带软件卸载教程 ，希望对你有帮助。
