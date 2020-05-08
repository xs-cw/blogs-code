---
title: "Docker相关问题"
date: 2020-05-05T22:05:31+08:00
tags: [docker,踩坑]
categories: [软件使用,问题]
draft: false
---

### docker for windows 启动kubernets问题

- 现象:
> docker desktop 启用kubernets后,一直处于`starting`状态.
- 原因:
> 启用后,kubernets所需镜像没有下载. 
- 解决:
> 建议卸载docker后,参照阿里云所提供的[流程](https://github.com/AliyunContainerService/k8s-for-docker-desktop).
> 重新安装docker,安装kubernets所需镜像,然后才启用kubernets.

### 在wsl中使用docker

 - 在wsl中安装`docker-cli`,`docker-compose`
 - 将`DOCKER_HOST=tcp://localhost:2375`写入wsl环境变量中
 - 在 windows的docker desktop中启用`Expose daeon on tcp:localhost:2375 without TLS`

### docker容器访问宿主机ip

- 新版docker中`host.docker.internal`代表宿主机,可以直接使用

