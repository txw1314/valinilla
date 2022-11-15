---
title: Electron的安装与使用
tags: Electron
categories: Electron
description: Electron的安装与使用
comments: true
top: false
pin: false
music:
  server: netease
  type: song
  id: 1916550868
date: 2022-08-04 00:46:00
updated: 2022-08-04 00:46:00
index_img: https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208040132020.jpeg
banner_img: https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208040132020.jpeg
headimg: https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208040132020.jpeg
img: https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208040132020.jpeg
cover: https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/202208040132020.jpeg
sticky:
---

# Electron 是使用 JavaScript, HTML 和 CSS 构建跨平台的桌面应用

本文基于 Windows 进行开发的过程，记录下来，以便日后使用，Electron 官网：https://electronjs.org/docs

## 1、安装 node.js

进入官网下载、安装。https://nodejs.org/en/

## 2、安装 cnpm

安装命令： `npm install -g cnpm --registry=https://registry.npm.taobao.org `

## 3、安装 Electron

安装命令：`cnpm install -g electron`

## 4、安装 Electron-forge

`Electron`工具整合项目：https://github.com/electron-userland/electron-forge

安装命令： `cnpm install -g electron-forge `

## 5、新建项目

F 盘新建`Electron`项目文件夹` F:Electron`。

在`Electron`文件夹下打开命令窗口来启动`cmd.exe`。

执行`electron-forge init <项目名称>`命令来生成名为 myapp 的项目文件夹，同时安装项目所需要的模块、依赖项等。

安装命令： `electron-forge init myapp `

## 6、启动项目

cd 到`myapp`目录下，执行命令`electron-forge start`来启动 app（也可以简单的用`npm start`来运行）。

## 7、项目文件

项目的目录结构：

> node_modules：文件夹下是各种模块、类库，

> src：app 的源代码文件，

> package.json：是描述包的文件。

> src/index.js：这是 app 主进程的入口，在这里创建了 mainWindow 浏览器窗口，使用 mainWindow.loadURL(file://${\_\_dirname}/index.html`)来加载 index.html 主页，

我们也可以在此链接我们需要链接的网址，来实现 web 桌面应用，例：mainWindow.loadURL(`https://www.cnblogs.com/`)，使用 mainWindow.webContents.openDevTools()`来打开开发者工具用于调试（这个操作通常在发布 app 时删除）。

然后是 app 的事件处理：

> ready：当`Electron`完成初始化后触发，这里初始化后就会去创建浏览器窗口并加载主页面。

> window-all-closed：当所有浏览器窗口被关闭后触发，一般此时就退出应用了。

> activate：当 app 激活时触发，一般针对 macOS 要需要处理。

> src/index.html：这是主页面，除了显示 Well hey there!!!的信息外，没什么具体内容。

## 8、package.json 配置

> "productName":"myapp" myapp 是打包后的文件名称

> "version":"1.0.0" 版本号

若想更换打包程序的图标，可以在 config->electronPackagerConfig->icon 中进行设置，

(例如：我们把 app.ico 放在 src 目录下就可以这样配置"icon":"src/favicon.ico"）

## 9、编译打包

输入以下命令进行编译打包： `npm run make `

修改`package.json`，在` electronPackagerConfig `部分添加` "asar": true `。

```
"electronPackagerConfig": {
	"asar": true
}
```

重新打包后源码文件会被打包进` app.asar `文件中（该文件仍然在 src 目录下）。

可以直接运行打包后的` myapp.exe `启动程序
