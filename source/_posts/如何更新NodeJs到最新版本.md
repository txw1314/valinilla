---
title: 如何更新NodeJs到最新版本？
author: 作者
tags: nodejs
categories: 软件
description: 如何更新NodeJs到最新版本？
comments: true
music:
  server: netease
  type: song
  id: 1916550868
date: 2026-06-25 14:05:13
updated: 2026-06-25 14:05:13
index_img:
banner_img:
headimg:
img:
cover:
---

# 如何更新NodeJs到最新版本？



# 你电脑上的NodeJs是怎么更新的？

## 前引

NodeJS更新迭代还是很频繁的，昨天在准备复习Vue3，根据官网示例新建一个Vue3的工程项目，项目内执行命令 `npm init vue@latest`，预期是这一指令将会安装并执行 `create-vue`，它是 Vue 官方的项目脚手架工具。

本人实际按此步骤操作之后，并没有成功生成项目。

在排查哪里出问题时，发现官网说了，需要本地安装了最新的 `NodeJS`，至少要16.0以上版本的，命令行 `node -v` 查了一下本地的 `NodeJS` 版本，发现是 12.18的。想着升级一下 `NodeJS`最新版吧，命令行执行 ~~`npm install node@latest / npm update node@latest`~~ ? 显然不是！ **本地电脑操作系统是window10**

![1.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/840e5817fe2740ba8a5055bffb624a04~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

> 附：升级npm到最新版本可以执行 `npm install npm@latest -g`

下面是我了解到的几种方式，供大家参考！

## 升级NodeJs方法一

方法一是很常规的做法，不借助第三方工具，window系统、苹果系统都适用。

就是去`Nodejs`官网下载最新版本，然后重新安装在原安装路径下（这样不用重新配环境变量），步骤如下：

1. 命令行里执行 `node -v`查看当前版本是否是最新版本
2. 查看之前的安装路径，使用命令 `where node`
3. 去[Nodejs官网](https://link.juejin.cn/?target=https%3A%2F%2Fnodejs.org%2Fen%2Fdownload%2F)下载匹配你电脑操作系统的最新的mis长期稳定版LTS，按步骤安装，安装路径是上一步的路径
4. 最后测试是否安装成功，执行`node -v`打印出版本信息

## 升级NodeJs方法二

方法二是使用工具 `nvmw` 或者 `nvm`，window系统的使用 `nvmw`，苹果系统的使用 `nvm`(*实际测试发现windows系统也可以安装nvm)*，步骤如下：

1. 安装 `nvmw`

```
npm install nvmw -g
```

1. 使用nvmw安装nodejs

```
nvmw install v18.12.0
```

1. 使用nvmw临时使用某个版本的nodejs

```
nvmw use v18.12.0
```

1. 使用nvmw切换本地的nodejs版本

```
nvmw switch v18.12.0
```

1. 查看本地安装的所有nodejs版本

```
nvmw ls
```

## 升级NodeJs方法三

在Linux系统通过包 `n`安装升级 NodeJs，步骤如下：

1. `sudo npm cache clean -f`
2. `sudo npm install n -g`
3. `sudo n stable / sudo n latest / sudo n 18.12.0`

## 升级NodeJs方法四

windows操作系统下，可使用工具 gnvm 管理NodeJs版本，步骤如下：

1. 首先安装gnvm

- 从Github下载安装 [32-bit](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2FKenshin%2Fgnvm-bin%2Fblob%2Fmaster%2F32-bit%2Fgnvm.exe%3Fraw%3Dtrue) 或者 [64-bit](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2FKenshin%2Fgnvm-bin%2Fblob%2Fmaster%2F64-bit%2Fgnvm.exe%3Fraw%3Dtrue)

1. 把下载的 gnvm.exe 文件放在NodeJs所在的安装目录，可通过 `where node` 查询；
2. 验证一下安装是否成功，执行 `gnvm version`
3. gnvm安装成功之后，用gnvm安装NodeJS的不同版本，gnvm会管理起来这些版本；

```js
js体验AI代码助手代码解读复制代码gnvm install latest
gnvm install 18.12.0
gnvm update latest
```

1. 查看安装了哪些NodeJs版本

```
gnvm ls
```

1. 切换不同的版本

```
gnvm use 18.12.0
```

1. 卸载不同的NodeJs版本

```
gnvm uninstall 18.12.0
```

## 小结

本文主要介绍了如何升级 NodeJs，提供了四种方法，不想使用第三方工具的话推荐使用第一种。 假如需要根据不同项目频繁切换Nodejs的版本，windows操作系统时可以选择方法二/四。
