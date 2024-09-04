---
title: git删除远程分支后，本地同步问题
author: 作者
tags: git
categories: 前端
description: git删除远程分支后，本地同步问题
comments: true
music:
  server: netease
  type: song
  id: 2101129701
date: 2022-11-01 10:00:18
updated: 2022-11-01 10:00:18
index_img: https://cdn.pixabay.com/photo/2020/07/05/05/12/sunset-5371719_1280.jpg
banner_img: https://cdn.pixabay.com/photo/2020/07/05/05/12/sunset-5371719_1280.jpg
headimg: https://cdn.pixabay.com/photo/2020/07/05/05/12/sunset-5371719_1280.jpg
img: https://cdn.pixabay.com/photo/2020/07/05/05/12/sunset-5371719_1280.jpg
cover: https://cdn.pixabay.com/photo/2020/07/05/05/12/sunset-5371719_1280.jpg
---

项目里不小心把本地分支给提交到了远程，而且名字还起错了，在删除远程分支后，发现

```
git branch
```

时，那个被删除的分支已经看不到，应该是被删除，然而在

```
git branch -a 
```

后，居然还能看到那个被删除的远程分支，求过某娘后，发现应该是本地未能同步的原因。
解决方法只有一行命令

```
git fetch -p
```


然后再看，果然没了。。。
