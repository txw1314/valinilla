---
title: git提交规范
author: 作者
tags: git
categories: 前端
description: git提交规范
comments: true
music:
  server: netease
  type: song
  id: 1916550868
date: 2022-11-02 02:07:11
updated: 2022-11-02 02:07:11
index_img:
banner_img:
headimg:
img:
cover:
---

### 1.windows 全局安装commitizennode模块
```
npm install -g commitizen@4.2.4
```

> 注意：一定要在当前windows用户下全局安装，**不是在项目内安装**

### 2.在需要使用Commitizen规范的项目内执行
注意前提该项目根目录上已有package.json文件

```
commitizen init cz-conventional-changelog --save --save-exact
or
commitizen init cz-conventional-changelog --save --save-exact --force

```


安装成功后检查package.json文件，如新增以下配置代表安装成功

```
"config": {
    "commitizen": {
    	"path": "./node_modules/cz-conventional-changelog"
    }
}
```

### 3.测试命令

```
git cz
```


显示（成功）：

 ```
 cz-cli@4.2.4, cz-conventional-changelog@3.3.0
 ? Select the type of change that you're committing: (Use arrow keys)
 
feat:     A new feature
fix:      A bug fix
docs:     Documentation only changes
style:    Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc) 
refactor: A code change that neither fixes a bug nor adds a feature
perf:     A code change that improves performance
test:     Adding missing tests or correcting existing tests
 (Move up and down to reveal more choices)
 ```

### 4.可自定义提交规范(汉化后可能涉及到无法进行校验)
#### 1、执行以下命令，并且在项目根目录创建.cz-config.js

```
$ npm i -D commitlint-config-cz  cz-customizable
```

#### 2、cz-config.js 文件（网上比较好的一个配置文件，可借鉴）
```
// 方案一
"use strict";
module.exports = {
  types: [
    { value: "✨特性", name: "特性:    一个新的特性" },
    { value: "🐛修复", name: "修复:    修复一个Bug" },
    { value: "📝文档", name: "文档:    变更的只有文档" },
    { value: "💄格式", name: "格式:    空格, 分号等格式修复" },
    { value: "♻️重构", name: "重构:    代码重构，注意和特性、修复区分开" },
    { value: "⚡️性能", name: "性能:    提升性能" },
    { value: "✅测试", name: "测试:    添加一个测试" },
    { value: "🔧工具", name: "工具:    开发工具变动(构建、脚手架工具等)" },
    { value: "⏪回滚", name: "回滚:    代码回退" },
  ],
  scopes: [
    { name: "模块1" },
    { name: "模块2" },
    { name: "模块3" },
    { name: "模块4" },
  ],
  messages: {
    type: "选择一种你的提交类型:",
    scope: "选择一个scope (可选):",
    // used if allowCustomScopes is true
    customScope: "Denote the SCOPE of this change:",
    subject: "短说明:\n",
    body: '长说明，使用"|"换行(可选)：\n',
    breaking: "非兼容性说明 (可选):\n",
    footer: "关联关闭的issue，例如：#31, #34(可选):\n",
    confirmCommit: "确定提交说明?",
  },
  allowCustomScopes: true,
  allowBreakingChanges: ["特性", "修复"],
  // limit subject length
  subjectLimit: 100,
};

// 方案二
module.exports = {
  // 可选类型
  types: [
    { value: 'feat', name: 'feat:     新功能' },
    { value: 'fix', name: 'fix:      修复' },
    { value: 'docs', name: 'docs:     文档变更' },
    { value: 'style', name: 'style:    代码格式(不影响代码运行的变动)' },
    {
      value: 'refactor',
      name: 'refactor: 重构(既不是增加feature，也不是修复bug)'
    },
    { value: 'perf', name: 'perf:     性能优化' },
    { value: 'test', name: 'test:     增加测试' },
    { value: 'chore', name: 'chore:    构建过程或辅助工具的变动' },
    { value: 'revert', name: 'revert:   回退' },
    { value: 'build', name: 'build:    打包' }
  ],
  // 消息步骤
  messages: {
    type: '请选择提交类型:',
    customScope: '请输入修改范围(可选):',
    subject: '请简要描述提交(必填):',
    body: '请输入详细描述(可选):',
    footer: '请输入要关闭的issue(可选):',
    confirmCommit: '确认使用以上信息提交？(y/n/e/h)'
  },
  // 跳过问题
  skipQuestions: ['body', 'footer'],
  // subject文字长度默认是72
  subjectLimit: 72
}


```

### 5.新建文件commitlint.config.js（若存在.commitlintrc.js文件，需先删除）

```
module.exports = {
        extends: [
                'cz'
        ]
}

```

### 6.使用git cz替代git commit
以后，凡是用到git commit命令，一律改为使用git cz。这时，就会出现选项，用来生成符合格式的 Commit message。
**注意：**使用之前，确保根目录下有.gitignore这个文件并且配置把node_modules目录pass掉，不然git add . 的时候会卡死

#### 执行git cz：![在这里插入图片描述](https://img-blog.csdnimg.cn/20201101213713533.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Zlc2ZzZWZncw==,size_16,color_FFFFFF,t_70#pic_center)

#### 选择一个fix作为测试：![在这里插入图片描述](https://img-blog.csdnimg.cn/20201101214146886.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Zlc2ZzZWZncw==,size_16,color_FFFFFF,t_70#pic_center)

翻译下意思就是说：
1.选择你要提交更改的类型
2.这个提交变化的范围（你的提交改动了哪些内容的意思）
3.写一篇简短的的描述，严谨的描述下这次的变化
4.提供下详细的变更描述
5.这个提交有破坏性的变化吗？
6.这个变化会影响一些开放的issue吗？

查看一下结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201101215345448.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Zlc2ZzZWZncw==,size_16,color_FFFFFF,t_70#pic_center)

