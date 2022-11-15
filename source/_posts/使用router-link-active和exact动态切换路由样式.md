---
title: 使用router-link-active和exact动态切换路由样式
author: 作者
tags: vue
categories: 前端
description: 使用router-link-active和exact动态切换路由样式
comments: true
music:
  server: netease
  type: song
  id: 1916550868
date: 2022-11-05 13:47:13
updated: 2022-11-05 13:47:13
index_img:
banner_img:
headimg:
img:
cover:
---

### 使用router-link-active和exact动态切换路由样式

每个router-link标签被点击时都有一个router-link-active的类，设置这个类的样式，就可以在vue里实现类的动态切换，在每个router-link标签里，都要加上exact这个属性，才能正常切换。

例子：

```
<template>
<div>
    <!-- 每个router-link标签里都要加上exact属性 -->
    <router-link :to="{name:'Home'}" exact><span>home</span></router-link>
    <router-link :to="{name:'Test'}" exact><span>Test</span></router-link>
    <router-link :to="{name:'News'}" exact><span>News</span></router-link>
</div>
</template>
<script>
export default {
  name: "CommonHeader",
  data () {
    return {
    };
  }
}
</script>
<style lang="css" scoped>
/* router-link标签会默认渲染为a标签 */
a{
    display: inline-block;
    width: 120px;
    height:50px ;
    line-height: 50px;
    text-decoration: none;
    color: #333;
}

/* 当router-link被点击时候的样式 */
.router-link-active{

      display: inline-block;
    width: 120px;
    height:50px ;
    line-height: 50px;
    text-decoration: none;
    color: #fff;
    background-color: red;
}
</style>
```
