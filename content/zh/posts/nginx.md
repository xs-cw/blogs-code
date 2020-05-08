---
title: "nginx相关"
date: 2020-05-05T22:05:31+08:00
tags: [nginx,踩坑]
categories: [nginx经验]
draft: false
---
### 使用docker nginx代理前端,避免跨域问题
- 使用dokcer-compose 启动nginx  
   `docker-compose.yml`配置:
   ``` yaml
   nginx:
       container_name: nginx
       image: nginx:latest
       ports: 
         - 80:80
         - 443:443
       volumes: 
         - ./conf/nginx:/etc/nginx/conf.d
         - ./log/nginx:/var/log/nginx
         - ./static:/var/www
   ``` 
   `nginx.conf`配置:  
     > **前端项目设置host header**  
       **`host.docker.internal`是docker宿主机ip**
   ```nginx
   server {
    listen 80;
    server_name localhost; 

    # 代理前端项目
    location / {
        proxy_set_header Host $host;
        #docker nginx必须这样设置
        proxy_pass http://host.docker.internal:8080;
    }

    # 代理后端接口
    location /api {
        # 接口地址修正
        rewrite ^/api/(.*)$ /$1 break;
        # 后端接口地址
        proxy_pass http://host.docker.internal:9090;
    }
   }
   ```