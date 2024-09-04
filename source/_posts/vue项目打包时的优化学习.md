---
title: vue项目打包时的优化学习
author: 作者
tags: 前端优化
categories: 前端
description: vue项目打包时的优化学习
comments: true
music:
  server: netease
  type: song
  id: 1403318151
date: 2022-11-04 00:14:29
updated: 2022-11-04 00:14:29
index_img: https://cdn.pixabay.com/photo/2017/12/12/21/17/doll-figures-3015495_1280.jpg
banner_img: https://cdn.pixabay.com/photo/2017/12/12/21/17/doll-figures-3015495_1280.jpg
headimg: https://cdn.pixabay.com/photo/2017/12/12/21/17/doll-figures-3015495_1280.jpg
img: https://cdn.pixabay.com/photo/2017/12/12/21/17/doll-figures-3015495_1280.jpg
cover: https://cdn.pixabay.com/photo/2017/12/12/21/17/doll-figures-3015495_1280.jpg
---

### 1.项目优化

##### 1.1项目可优化的内容

- 生成打包报告
- 第三方库启用CDN
- Element-ui组件按需加载
- 路由懒加载
- 首页内容定制

#### 1.2页面顶部进度条效果

使用nprogess第三方库

在axios请求拦截器中触发
 Nprogress.start()

在axios响应拦截器中触发
 Nprogress.done()

#### 1.3 打包时的优化

##### 1.3.1清除console

使用babel-plugin-transform-remove-console

```csharp
安装：npm install babel-plugin-transform-remove-console --save-dev
```

```cpp
.babelrc: 
// 全部清除console

{
  "plugins": ["transform-remove-console"]
}
```



```json
// with options选择性删除

{
  "plugins": [ ["transform-remove-console", { "exclude": [ "error", "warn"] }] ]
}
```

##### 1.3.2 区分开发和生产环境下使用 babel-plugin-transform-remove-console



```java
// babel.config.js文件里

// 定义一个生产环境的插件数组

const prodPlugins = []

// 如果是生产环境则添加'transform-remove-console'

if (process.env.NODE_ENV === 'production') {

  prodPlugins.push('transform-remove-console')

}

module.exports = {

  presets: [

    '@vue/cli-plugin-babel/preset'

  ],

  plugins: [

    [

      'component',

      {

        libraryName: 'element-ui',

        styleLibraryName: 'theme-chalk'

      }

    ],

    // 将生产环境的数组展开到配置中

    ...prodPlugins

  ]

}
```

#### 1.4 生成打包报告

打包时，为了直观地发现项目中存在的问题，可以生成打包报告。

##### 1.4.1 通过命令行参数的形式生成报告

```cpp
// 通过vue-cli的命令选项可以生成打包报告

// --report选项可以生成report.html以帮助分析报告内容

vue-cli-service build --report
```

##### 1.4.2 通过可视化的UI面板直接查看报告

  通过仪表盘和分析面板可以看到加载速度和依赖项资源大小占比，从而进一步优化。

![img](https:////upload-images.jianshu.io/upload_images/24637569-62f27e814bd6fef6.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)



##### 1.5 通过vue.config.js修改webpack的默认配置

  vue-cli3.0+工具生成的项目，默认隐藏了所有webpack的配置项，这样做的目的时屏蔽项目中的所有配置，让重心放在项目功能和业务逻辑上，省去配置带了的各种繁琐配置事项。

> vue.config.js官方文档：[vue.config.js官方文档](https://links.jianshu.com/go?to=https%3A%2F%2Fcli.vuejs.org%2Fzh%2Fconfig%2F%23%E5%85%A8%E5%B1%80-cli-%E9%85%8D%E7%BD%AE)

##### 1.6 为开发模式与发布模式指定不同的打包入口

  默认情况下，vue项目中的开发模式和发布模式，共同使用哟个打包的入口文件（src/main.js）。为了分离开发陌生和发布模式，可以指定不同的打包入口文件。

- 开发模式的入口文件为src/main-dev.js
- 生产模式的入口文件为src/main-prod.js

###### 1.6.1 configureWebpack和chainWebpack

在vue.config.js中，新增configureWebpack和chainWebpack节点自定义打包配置。
 configureWebpack和chainWebpack作用相同。唯一的区别是修改方式不同：
 ① chainWebpack链式编程形式，来改变webpack的默认配置
 ② configureWebpack通过操作对象的形式，来改变webpack的默认配置

> 参考vue.config.js官方文档：[vue.config.js官方文档](https://links.jianshu.com/go?to=https%3A%2F%2Fcli.vuejs.org%2Fzh%2Fconfig%2F%23%E5%85%A8%E5%B1%80-cli-%E9%85%8D%E7%BD%AE)

###### 1.6.2 通过chainWebpack自定义打包入口

代码示列：

```tsx
// vue.config.js
module.exports = {
    chainWebpack:config=>{
        //发布模式
        config.when(process.env.NODE_ENV === 'production',config=>{
            //entry找到默认的打包入口，调用clear则是删除默认的打包入口
            //add添加新的打包入口
            config.entry('app').clear().add('./src/main-prod.js')
        })
        //开发模式
        config.when(process.env.NODE_ENV === 'development',config=>{
            config.entry('app').clear().add('./src/main-dev.js')
        })
    }
}
```

##### 1.7 通过extrenals加载外部CDN资源

默认情况下，通过import语法导入的第三方依赖包，最终会被打包合并到同一个文件中，从而导致打包成功后的文件体积过大。
 解决办法：通过webpack的externals节点，来配置并加载外部的CDN资源，凡是声明在externals中的第三方依赖包，都不会被打包。
 **步骤一：声明需要外部CDN的项目**

```csharp
//使用externals设置排除项
config.set('externals',{
  vue:'Vue',
  'vue-router':'VueRouter',
  axios:'axios',
  lodash:'_',
  echarts:'echarts',
  nprogress:'NProgress',
  'vue-quill-editor':'VueQuillEditor'
})
```

**步骤二：在public/index.html文件头部添加CDN样式css资源**

```xml
<!-- nprogress 的样式表文件 -->
<link rel="stylesheet" href="https://cdn.staticfile.org/nprogress/0.2.0/nprogress.min.css" />
<!-- 富文本编辑器 的样式表文件 -->
<link rel="stylesheet" href="https://cdn.staticfile.org/quill/1.3.4/quill.core.min.css" />
<link rel="stylesheet" href="https://cdn.staticfile.org/quill/1.3.4/quill.snow.min.css" />
<link rel="stylesheet" href="https://cdn.staticfile.org/quill/1.3.4/quill.bubble.min.css" />
```

**步骤三：在public/index.html文件头部添加CDN样式js资源**

```xml
<script src="https://cdn.staticfile.org/vue/2.5.22/vue.min.js"></script>
<script src="https://cdn.staticfile.org/vue-router/3.0.1/vue-router.min.js"></script>
<script src="https://cdn.staticfile.org/axios/0.18.0/axios.min.js"></script>
<script src="https://cdn.staticfile.org/lodash.js/4.17.11/lodash.min.js"></script>
<script src="https://cdn.staticfile.org/echarts/4.1.0/echarts.min.js"></script>
<script src="https://cdn.staticfile.org/nprogress/0.2.0/nprogress.min.js"></script>
<!-- 富文本编辑器的 js 文件 -->
<script src="https://cdn.staticfile.org/quill/1.3.4/quill.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/vue-quill-editor@3.0.4/dist/vue-quill-editor.js"></script>
```

##### 1.8 通过CDN优化ElementUi的打包

操作流程如下：
 ① 在main.js入口文件，注释掉element-ui的加载代码
 ② 在index.thml的头部区域中，通过CDN加载element-ui的js和css样式

```xml
<!-- element-ui 的样式表文件 -->
<link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.8.2/theme-chalk/index.css" />
<!-- element-ui 的 js 文件 -->
<script src="https://cdn.staticfile.org/element-ui/2.8.2/index.js"></script>
```

##### 1.9 首页内容定制(按需渲染)

开发环境的首页和发布环境的首页展示内容的形式有所不同。
 如开发环境中使用的是import加载第三方包，而发布环境则是使用CDN，那么首页也需根据环境不同来进行不同的实现。
 可以通过插件的方式来定制首页内容，打开vue.config.js，编写代码如下：

```tsx
module.exports = {
    chainWebpack:config=>{
        config.when(process.env.NODE_ENV === 'production',config=>{
            ......
            
            // 使用htmlWebpackPlugin插件
            config.plugin('html').tap(args=>{
                // 添加参数isProd，通过isProd来判断是否渲染
                args[0].isProd = true
                return args
            })
        })

        config.when(process.env.NODE_ENV === 'development',config=>{
            config.entry('app').clear().add('./src/main-dev.js')

            // 使用插件
            config.plugin('html').tap(args=>{
                // 添加参数isProd
                args[0].isProd = false
                return args
            })
        })
    }
}
```

然后在public/index.html中使用插件判断是否为发布环境并定制首页内容:

```xml
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <link rel="icon" href="<%= BASE_URL %>favicon.ico">
    <title><%= htmlWebpackPlugin.options.isProd ? '' : 'dev - ' %>电商后台管理系统</title>

    <% if(htmlWebpackPlugin.options.isProd){ %>
    <!-- nprogress 的样式表文件 -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/nprogress/0.2.0/nprogress.min.css" />
    ........
    <!-- element-ui 的 js 文件 -->
    <script src="https://cdn.staticfile.org/element-ui/2.8.2/index.js"></script>
    <% } %>
  </head>
```

#### 2. 项目上线

##### 2.1 项目上线相关配置

1. 通过nodejs创建web服务器
2. 开启gzip压缩配置
3. 配置https服务
4. 使用pm2管理应用

##### 2.1.1 通过node创建web服务器

创建node项目，并安装express，通过express快速下黄健web服务器，将打包的vue项目，托管为静态资源。
 代码如下：

```tsx
const express = require('express')

const app = express()

app.use(express.static('./dist'))

app.listen(8998,()=>{
    console.log("server running at http://127.0.0.1:8998")
})
```

###### 2.1.2 开启gzip配置

使用gzip可以减小文件体积，是传输速度更快。
 可以通过服务端使用express做gzip，配置如下：

```tsx
// 安装compression ：npm i compression -D
const express = require('express')
// 导入包
const compression = require('compression')

const app = express()
// 启用中间件
app.use(compression())
app.use(express.static('./dist'))

app.listen(8998,()=>{
    console.log("server running at http://127.0.0.1:8998")
})
```

###### 2.1.3 配置HTTPS服务

配置https服务一般是后台进行处理，前端开发人员了解即可。
 首先，需要申请SSL证书，进入[https://freessl.cn](https://links.jianshu.com/go?to=https%3A%2F%2Ffreessl.cn)官网
 在后台导入证书，打开今天资料/素材，复制素材中的两个文件到vue_shop_server中
 打开app.js文件，编写代码导入证书，并开启https服务

```jsx
const express = require('express')
const compression = require('compression')
const https = require('https')
const fs = require('fs')

const app = express()
//创建配置对象设置公钥和私钥
const options = {
    cert:fs.readFileSync('./full_chain.pem'),
    key:fs.readFileSync('./private.key')
}

app.use(compression())
app.use(express.static('./dist'))

// app.listen(8998,()=>{
//     console.log("server running at http://127.0.0.1:8998")
// })

//启动https服务
https.createServer(options,app).listen(443)
```

###### 2.1.4 使用pm2管理应用

打开vue_shop_server文件夹的终端，输入命令：npm i pm2 -g
 使用pm2启动项目，在终端中输入命令：pm2 start app.js --name 自定义名称
 查看项目列表命令：pm2 ls
 重启项目：pm2 restart 自定义名称
 停止项目：pm2 stop 自定义名称
 删除项目：pm2 delete 自定义名称

