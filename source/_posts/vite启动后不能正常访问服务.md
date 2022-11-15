---
title: vite启动后不能正常访问服务
author: 作者
tags: vite
categories: 前端
description: 当使用 `Vite `构建项目后，需要通过局域网中的电脑或手机访问服务调试时，发现通过 IP + 端口无法访问。
comments: true
music:
  server: netease
  type: song
  id: 441491828
date: 2022-10-16 13:00:43
updated: 2022-10-16 13:00:43
index_img: https://t7.baidu.com/it/u=1819248061,230866778&fm=193&f=GIF
banner_img: https://t7.baidu.com/it/u=1819248061,230866778&fm=193&f=GIF
headimg: https://t7.baidu.com/it/u=1819248061,230866778&fm=193&f=GIF
img: https://t7.baidu.com/it/u=1819248061,230866778&fm=193&f=GIF
cover: https://t7.baidu.com/it/u=1819248061,230866778&fm=193&f=GIF
---

### 起因
当使用 `Vite `构建项目后，需要通过局域网中的电脑或手机访问服务调试时，发现通过 IP + 端口无法访问。

### 问题重现
当运行 `npm run dev | serve `命令时，会显示一下内容。

```
vite-vue@0.0.0 serve /Users/UserName/Workspace/vue-vite
vite | vite preview

  vite v2.3.7 build preview server running at:

  > Local: http://localhost:3000 | 5000/
  > Network: use `--host` to expose
```

### 问题原因

当 局域网 中另一台设备需要访问该服务时，必须通过本机 IP + 端口 访问。
尝试访问后，发现找不到这个服务，原因是 没有 将服务暴露在网络中

### 解决方法
在控制台会显示 `user --host to expose`（使用 --host 暴露网络）
通常我们都会在`npm run dev | serve ` 的后边拼接上` --host`

执行` npm run dev | serve --host` 后控制台还是会显示 `Netvork: user --host to expose`

```
server.host
类型： string
默认： ‘127.0.0.1’
指定服务器应该监听哪个 IP 地址。 如果将此设置为 0.0.0.0 将监听所有地址，包括局域网和公网地址。
```

于是通过查阅 文档 发现了三种解决方案：

### 1.修改 `vite.config.js` 配置

在根目录下的 vite.config.js 文件中添加以下内容(第一种不一定有效，试用其他方法)

```
import vue from '@vitejs/plugin-vue'

/**
 * https://vitejs.dev/config/
 * @type {import('vite').UserConfig}
 */
 export default {
     plugins: [vue()],
     server: {                // ← ← ← ← ← ←
     host: '0.0.0.0'    // ← 新增内容 ←
     }                        // ← ← ← ← ← ←
 }
```

### 2.通过 `Vite CLI` 配置
执行 `npx vite --host 0.0.0.0` 命令后，就可以通过 `http://10.56.116.128:3000/ `访问了

```
  vite v2.3.7 dev server running at:

  > Local:    http://localhost:3000/
  > Network:  http://10.56.116.128:3000/

  ready in 301ms.
```

### 3.修改 `npm` 脚本
修改 `package.json `文件中` scripts` 节点下的脚本，如下：

```
"scripts": {
  "dev": "vite --host 0.0.0.0",
  "build": "vite build",
  "serve": "vite preview --host 0.0.0.0"
}
```

