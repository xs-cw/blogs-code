---
title: "WSL踩坑"
date: 2020-03-11T19:29:24+08:00
tags: [wsl,踩坑]
categories: [软件使用,问题]
draft: false
---

### wsl ubuntu 更新中断
  更新中断后部分软件安装会报错,可以先将`/var/lib/dpkg/info`目录下对应的文件备份
  然后再重新更新.
  ```bash
  sudo mv /var/lib/dpkg/info/{pkg}.postinst /var/lib/dpkg/info/{pkg}.postinst.bak
  ```
