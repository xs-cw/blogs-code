---
title: "系统安装找到启动路径"
date: 2020-03-04T21:05:39+08:00
tags: [系统]
categories: [系统,系统安装]
draft: false
---
windows 系统安装启动盘启动时找不到启动路径
1. 找BOOTMGR文件在那个盘符`find /bootmgr`
2. 这样会在所有的磁盘根目录寻找文件，找到文件后接着进入该盘符 `root (hd0,0)`
3. 然后转交引导权`chainloader /bootmgr`
   再执行`boot`
   启动
这样就OK了~！

 