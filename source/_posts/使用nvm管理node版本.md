---
title: 使用nvm管理node版本
author: 作者
tags: nvm
categories: 前端
description: 使用nvm管理node版本
comments: true
music:
  server: netease
  type: song
  id: 28754098
date: 2022-10-29 15:50:04
updated: 2022-10-29 15:50:04
index_img: https://t7.baidu.com/it/u=12235476,3874255656&fm=193&f=GIF
banner_img: https://t7.baidu.com/it/u=12235476,3874255656&fm=193&f=GIF
headimg: https://t7.baidu.com/it/u=12235476,3874255656&fm=193&f=GIF
img: https://t7.baidu.com/it/u=12235476,3874255656&fm=193&f=GIF
cover: https://t7.baidu.com/it/u=12235476,3874255656&fm=193&f=GIF
---

# nvm安装及配置使用

![使用nvm管理node版本，一条龙解决前端开发环境配置](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d63a5ec6ab5546e5ba5508cab1d06eca~tplv-k3u1fbpfcp-zoom-crop-mark:3024:3024:3024:1702.awebp?)

> nvm是node版本管理器，用于管理多个活动Node.js版本的简单bash脚本，让我们可以设置默认node版本，并在不同开发环境中切换不同版本。

### 安装nvm

1.打开[下载地址](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fcoreybutler%2Fnvm-windows%2Freleases)，下载对应安装包。

![nvm-1.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ad6e6d7e25274b2c9993fd18cd4e4c92~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

2.双击安装文件 nvm-setup.exe，同意协议点击下一步

![nvm-2.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a3a8519fb19048229116922ba34e4e22~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

3.选择nvm安装路径

![nvm-3.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0abaa08a438e41ff93f4db2d21bd3d0c~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

4.选择nodejs路径

![nvm-4.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/53dac6249cf2468a8bc75df4fbd8128f~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

5.点击安装按钮进行安装

![nvm-5.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9fabbe3cf59b4b33a231edf6477bfbcc~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

6.安装完毕打开控制台，输入`nvm`，安装成功则如下显示。

![nvm-8.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4214fa2569b643d3a2d863a93e4a9ef2~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

### 解决nvm安装node和npm太慢

> nvm默认node镜像源是`https://nodejs.org/dist`，从默认的镜像缘源下载会很慢，所以可以通过更换镜像源加快下载

1.找到之前安装nvm的文件夹目录，打开`settings.txt`文件

![nvm-6.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b39ca9dfdce24da4985fc1473d88905d~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

2.新增两行配置，更换`node`和`npm`的下载源为淘宝镜像源

```sh
node_mirror: https://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/
复制代码
```

![nvm-7.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/07320215fb8d4a489ddc91b7cd03ac97~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

### 使用nvm安装Node.js

1.终端输入`nvm ls`查看已安装的`node.js`版本。`*`选择的为当前使用的版本。

```sh
nvm ls
```

![nvm-9.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/703890f9115f42b1b875020233760369~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

2.使用`nvm`安装指定版本`node.js`

```sh
nvm install 14.17.6
```

如下图所示说明安装指定版本的node.js和npm成功

![nvm-10.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b9d1e3757ff0436d802e7801b80b8472~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

在nvm的文件夹目录新增了指定版本的文件夹

![nvm-11.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c1f7b247bb674fa99452a3aff40f1798~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

文件夹里有已经安装好的`node`、`npm`和`npx`的包

![nvm-12.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/972feb22a6d5436087ecb54e71ae08b2~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

3.使用指定版本`node.js`，查看`node`和`npm`版本。

```sh
nvm use 14.17.6
```

![nvm-13.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6a51e6d2193149b4b1770cf30743b025~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

4.卸载指定版本`node.js`

```sh
nvm uninstall 14.17.6
```

### 命令提示说明

- `nvm arch [32|64]`：显示node是运行在32位还是64位。
- `nvm current`： 显示活动版本。
- `nvm install <version> [arch]`：安装node， version是特定版本也可以是最新稳定版本latest。可选参数arch指定安装32位还是64位版本，默认是系统位数。可以添加--insecure绕过- 远程服务器的SSL。
- `nvm list [available]`：显示已安装的列表。可选参数available，显示可安装的所有版本。list可简化为ls。
- `nvm on`：开启node.js版本管理。
- `nvm off`：关闭node.js版本管理。
- `nvm proxy [url]`：设置下载代理。不加可选参数url，显示当前代理。将url设置为none则移除代理。
- `nvm uninstall <version>`：卸载指定版本node。
- `nvm use [version] [arch]`：使用制定版本node。可指定32/64位。
- `nvm root [path]`：设置存储不同版本node的目录。如果未设置，默认使用当前目录。
- `nvm version`：显示nvm版本。version可简化为v。
- `nvm node_mirror [node_mirror_url]`：设置node镜像。默认是`https://nodejs.org/dist/`。如果不写url，则使用默认url。设置后可至安装目录settings.txt文件查看，也可直接在该文件操作。
- `nvm npm_mirror [npm_mirror_url]`：设置npm镜像。默认是`https://github.com/npm/cli/archive/`。如果不写url，则使用默认url。设置后可至安装目录settings.txt文件查看，也可直接在该文件操作。

### 安装yarn

1.使用已经安装好的`npm`来安装`yarn`

```sh
npm install yarn -g
```

2.查看`yarn`版本

```sh
yarn -v
```

![nvm-14.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9cb37ad19c81451b8de97bdd961f30e4~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

3.使用`nvm`进行`node版本`管理后，在每个`node版本`下都需要安装`yarn`，安装后指定版本文件夹会新增`yarn`文件

![nvm-15.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/37656e7512bb4656b40fb1e7ba948d98~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?)

### 设置npm和yarn的淘宝镜像

> 淘宝 NPM 镜像是一个完整 npmjs.org 镜像，你可以用此代替官方版本(只读)大幅提升包的下载速度，同步频率目前为 10分钟 一次以保证尽量与官方服务同步。

1.设置`npm`淘宝镜像

```sh
npm config set registry http://registry.npm.taobao.org/
```

2.设置`yarn`淘宝镜像

```sh
yarn config set registry http://registry.npm.taobao.org/
```

3.查询当前配置的镜像

```sh
npm get registry
yarn config get registry
```
