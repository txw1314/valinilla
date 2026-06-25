---
title: 查看Windows11的激活状态和到期时间
author: 作者
tags: window
categories: 软件
description: 查看Windows11的激活状态和到期时间
comments: true
music:
  server: netease
  type: song
  id: 1916550868
date: 2026-06-25 14:03:56
updated: 2026-06-25 14:03:56
index_img:
banner_img:
headimg:
img:
cover:
---

## **可以通过命令提示符或系统设置查看 Windows 11 的激活状态和到期时间，永久激活会显示“永久激活”，批量激活会显示剩余有效期。**

## 方法一：使用命令提示符查询

1. 按 **Win + R** 打开运行窗口，输入 **cmd** 并按回车，打开命令提示符。

2. 输入命令

    

   ```
   slmgr /xpr
   ```

    

   并按回车。

   - 如果系统永久激活，会弹出窗口显示“计算机已永久激活”。
   - 如果是批量激活（KMS），会显示具体的到期日期。

3. 若需要查看更详细的激活信息，包括激活ID、安装ID、部分产品密钥和激活时间，可输入命令 `slmgr.vbs -dlv` 并按回车，弹出的窗口中会显示“激活截止日期”或“Last Activation Date”相关信息
