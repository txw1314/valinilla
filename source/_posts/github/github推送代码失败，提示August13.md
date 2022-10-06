---
title: github推送代码失败，提示August13
author: vanilla
tags: github
categories: github
description: github推送代码失败，提示August13
comments: true
music:
  server: netease
  type: song
  id: 1916550870
date: 2022-10-02 01:23:52
updated: 2022-10-02 01:23:52
index_img:
banner_img:
headimg:
img:
cover:
---
解决 remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.

##### 问题原因

```
Logon failed, use ctrl+c to cancel basic credential prompt.
remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
fatal: Authentication failed for 'https://github.com/dream-code-kangli/online-learning.git/'

```

> 意思是自从 21 年 8 月 13 后不再支持用户名密码的方式验证了，需要创建个人访问令牌(personal access token)。

### 解决方法

在 GitHub 上生成令牌，应用于所需的仓库中

### 1、点击 settings

![在这里插入图片描述](https://img-blog.csdnimg.cn/bfa6e2fca5f2405aacfeb5e35e08faae.png#pic_center)

### 2、点击右侧的 Developer settings

![在这里插入图片描述](https://img-blog.csdnimg.cn/6302aea973bd4c75bceac6af73865020.png#pic_center)

### 3、点击 Personal access tokens(个人访问令牌)

![在这里插入图片描述](https://img-blog.csdnimg.cn/d99833c67b1f4c6f87c3b7d58586cdc6.png#pic_center)

### 4、点击 Generate new token

![在这里插入图片描述](https://img-blog.csdnimg.cn/6dbaf67511904ffe8a8375299ae338ed.png#pic_center)

### 5、设置 token 信息

![在这里插入图片描述](https://img-blog.csdnimg.cn/31bfbbbf974542b0bef14f272783e499.png#pic_center)


根据所需过期时间，建议设置成永远，以免麻烦，建议所有选项都选上

点击 Generate token 生成令牌

### 6、得到生成的令牌

![在这里插入图片描述](https://img-blog.csdnimg.cn/3e42a4e2f4cf4e08bc7716606e05f319.png#pic_center)

### 7、应用令牌
将生成的令牌拷贝下来，记得保存，下次你就看不到了。

修改现有的 url

```
git remote set-url origin  https://<your_token>@github.com/<USERNAME>/<REPO>.git

eg: git remote set-url origin http://ghp_tP3EgFiUWqeHL16Dmy1vkswpZVUUnO4RkQZ 2@github.com/txw1314/valinilla.git
```

将<your_token>换成你自己得到的令牌。<USERNAME>是你自己github的用户名，<REPO>是你的项目名称

> tip:<>不用带上，直接写自己的令牌和仓库名称就行了

然后再次执行 pull push 操作，输入你的gitbub用户名，密码是生成的令牌，大功告成。

<style>
h1,h2,h3,h4,h5,h6{
	text-align:center;
    list-style: none;
}
</style>

