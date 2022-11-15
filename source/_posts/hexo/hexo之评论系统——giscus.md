---
title: hexo之评论系统——giscus
tags:
  - 评论系统
  - giscus
categories: Hexo系列
type: categories
description: hexo之评论系统——giscus
date: 2022-07-31 01:08:28
# 文章头图设置
index_img: https://img1.baidu.com/it/u=2688422801,1696196797&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
banner_img: https://img1.baidu.com/it/u=2688422801,1696196797&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
headimg: https://img1.baidu.com/it/u=2688422801,1696196797&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
img: https://img1.baidu.com/it/u=2688422801,1696196797&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
cover: https://img1.baidu.com/it/u=2688422801,1696196797&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500
music:
  server: netease
  type: song
  id: 1330348068
---

本篇主要讲的是 hexo 主题 volantis 的评论系统相关的 giscus

# 一、评论系统的选择 giscus

## 1.1 打开文件\_config.volantis.yml，搜索 comments 评论部分，可以看到这里选择的是 giscus

```
comments:
  title: <i class='fa-solid fa-comments'></i> 评论
  subtitle:
  service: giscus
  # 可选评论系统 #
```

## 1.2 继续搜索 giscus，显示需要配置一些 repo/repo-id 等参数

```
  # giscus
  # https://giscus.app
  # https://github.com/laymonage/giscus
  giscus:
    # 以下配置按照 yml 格式增删填写即可
    repo: txw1314/comment-giscus
    repo-id: R_kgDOHvE8vw
    category: Comments
    category-id: DIC_kwDOHvE8v84CQgFl
    mapping: "title"
    reactions-enabled: "1"
    emit-metadata: "0"
    position: "top"
    loading: "lazy"
    crossorigin: "anonymous"
    lang: "zh-CN"
    # 以上配置按照 yml 格式增删填写即可
```

# 二、如何获取 giscus 的相关配置

## 2.1 在 github 的操作

### 2.1.1 新建一个关于评论的仓库

我这里命名的是 comment-giscus,点击 Setting

![image-20220801220102126](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801220102126.png)

### 2.1.2 继续往下滚动到 Features，勾选 Wikis

![image-20220801220132464](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801220132464.png)

### 2.1.3 继续滚动，勾选 Discussions。

![image-20220801220200017](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801220200017.png)

## 2.2 在 GitHub 代码库上的讨论页面创建一个类别

> 比如 “Comments（评论）”——或者选择现有的类别。

![image-20220801220348443](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801220348443.png)

### 2.2.1 如果没有，那就新建类别

![image-20220801220447606](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801220447606.png)

### 2.2.2 填写 title 和详情，点击 create 创建完成

![image-20220801220619536](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801220619536.png)

### 2.2.3 创建完成，分类里面有了我们新增的分类

![image-20220801220734420](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801220734420.png)

## 2.3 转到 https://github.com/apps/giscus，按照提示操作，并仅授予对选定代码库的访问权限。

### 2.3.1 安装 giscus

> 在根目录安装 giscus : `npm install giscus`

![image-20220801220808104](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801220808104.png)

### 2.3.2 选择建立的评论仓库

![image-20220801220955798](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801220955798.png)

### 2.3.3 确认账号密码

![image-20220801221013850](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801221013850.png)

### 2.3.4 选择完成

![image-20220801221043339](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801221043339.png)

## 2.4 在 giscus 的操作，我们需要配置 giscus 的小部件。

> 打开网页：[giscus](https://giscus.app/zh-CN)

### 2.4.1 选择语言和仓库，

输入之前 github 创建仓库名称，如用`username/reponame`，这里包括用户名和仓库名称，

> 注意/前后不能有空格，不能输错，否则下面会提示报错

![image-20220801221204482](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801221204482.png)

### 2.4.2 页面映射关系，这里我选择的是第三个

![image-20220801221317913](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801221317913.png)

### 2.4.3 然后选择 Discussion 分类和特性

分类选择我们上面新建的分类，特性我选择了箭头不两个，也可不选，主题随便选一个就行，不选也没关系这个不影响

![image-20220801221551343](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801221551343.png)

![image-20220801221621379](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801221621379.png)

### 2.4.4 启用 giscus

一切就绪之后，Giscus 将根据你的设置生成一个脚本标签，这就是我们想要的 giscus 的配置信息了。你可以将其粘贴到你的代码中，记得把这个保存下来，不然还要在操作一下这步骤重新生成了

![image-20220801221745879](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801221745879.png)

## 这是最终结果

![image-20220801221831472](https://jsd.cdn.zzko.cn/gh/txw1314/blog-img@main/img/image-20220801221831472.png)
