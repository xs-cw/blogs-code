---
title: "Docker-Compose安装出错"
date: 2020-03-04T21:05:39+08:00
tags: [docker-compose]
categories: [软件使用,docker]
draft: false
---
**1、安装docker-compose**

1. 首先检查Linux有没有安装Python-pip包，直接执行 `yum install python-pip`

1. 没有python-pip包就执行命令 `yum -y install epel-release`

1. 执行成功之后，再次执行`yum install python-pip`

1. 对安装好的pip进行升级 `pip install --upgrade pip`

1. 安装好pip之后，就可以安装Docker-Compose了.  
1. 在linunx终端执行：`pip install docker-compose`



执行完之后，输入`docker-compse -version`，报如下错误

```bash
Traceback (most recent call last):
  File "/usr/bin/docker-compose", line 7, in <module>
    from compose.cli.main import main
  File "/usr/lib/python2.7/site-packages/compose/cli/main.py", line 17, in <module>
    import docker
  File "/usr/lib/python2.7/site-packages/docker/__init__.py", line 2, in <module>
    from .api import APIClient
  File "/usr/lib/python2.7/site-packages/docker/api/__init__.py", line 2, in <module>
    from .Client import APIClient
...
    
```





**2、解决方法：**

卸载已经安装的Python的urllib3包

```bash
pip uninstall urllib3
```

然后就能够成功安装python-urllib3软件包

**3、运行certbot命令提示urllib3版本低**

如果你成功安装了python-urllib3软件包，在运行certbot命令时提示urllib3版本太低，可以使用pip命令升级urllib3包：

```bash
pip install --upgrade urllib3
```

执行成功之后：`docker-compose  --version` 查看版本信息.

```bash
 $docker-compose -version 
 docker-compose version 1.8.1, build 878cff1  
```





本文来自[博客园](https://www.cnblogs.com)

感谢作者[Richie`](https://home.cnblogs.com/u/richiewlq/)

查看原文[CentOS7下安装Docker-Compose No module named 'requests.packages.urllib3'](https://www.cnblogs.com/richiewlq/p/9203504.html)
