---
title: "git相关"
date: 2020-05-05T22:05:31+08:00
tags: [git]
categories: [git]
draft: false
---
### git添加多个远程
```bash
# 添加远端, 一次push到多个仓库
git remote set-url --add origin https://github.com/example/test.git
# 查看远端仓库
git remote -v
# 添加远端仓库,pull/push时需要指定
git remote set-url --add other https://other.test.com/zxbetter/test.git
```
### git 贮藏
```bash
git stash save "stash info"
git stash pop
```