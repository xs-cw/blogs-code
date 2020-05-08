---
title: "跨域问题"
date: 2020-05-05T22:05:31+08:00
tags: [前端,后端]
categories: [前端]
draft: false
---
### 前端项目跨域问题
- 问题:
前端请求与页面地址不在同一域内.  
`sechma://host:port`如:`http://localhost:8080`
三者有一个不相同都属于跨域.  
- 解决方案1: 后端新增拦截器或者中间件,允许跨域请求
   如 `gin`框架:
   在路由上使用以下中间件
```go
func Cors() gin.HandlerFunc {
	return func(c *gin.Context) {
		method := c.Request.Method

		c.Header("Access-Control-Allow-Origin", "*")
		c.Header("Access-Control-Allow-Headers", "Content-Type,AccessToken,X-CSRF-Token, Authorization, Token")
		c.Header("Access-Control-Allow-Methods", "POST, GET, OPTIONS")
		c.Header("Access-Control-Expose-Headers", "Content-Length, Access-Control-Allow-Origin, Access-Control-Allow-Headers, Content-Type")
		c.Header("Access-Control-Allow-Credentials", "true")

		//放行所有OPTIONS方法
		if method == "OPTIONS" {
			c.AbortWithStatus(http.StatusNoContent)
		}
		// 处理请求
		c.Next()
	}
}
```
- 解决方案2: nginx代理前端  
   nginx配置如下:
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