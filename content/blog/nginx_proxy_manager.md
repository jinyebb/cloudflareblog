+++
title = "Nginx Proxy Manager安装"
date = "2023-07-13T22:38:57+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++


**1.安装Docker和Docker-Compose** 

[Docker安装文档](https://docs.docker.com/get-docker/) 

[Docker-Compose安装文档](https://docs.docker.com/compose/install/)


**2.配置Nginx Proxy Manager安装文件**

```
##新建应用存放目录
mkdir -p docker/data/nginx_proxy_manager
##进入该目录
cd docker/data/nginx_proxy_manager
```

***创建docker-compose.yml 粘贴以下配置信息，如报错，version: '3.8'改成'3.3'***

```
version: '3.8'
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      # These ports are in format <host-port>:<container-port>
      - '80:80' # Public HTTP Port
      - '443:443' # Public HTTPS Port
      - '81:81' # Admin Web Port
      # Add any other Stream port you want to expose
      # - '21:21' # FTP

    # Uncomment the next line if you uncomment anything in the section
    # environment:
      # Uncomment this if you want to change the location of
      # the SQLite DB file within the container
      # DB_SQLITE_FILE: "/data/database.sqlite"

      # Uncomment this if IPv6 is not enabled on your host
      # DISABLE_IPV6: 'true'

    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```

**3.安装/运行Nginx Proxy Manager**

```
docker-compose up -d
```

```
##管理界面地址
http://127.0.0.1:81
```

```
##默认管理员账号/密码
Email:admin@example.com
Password:changeme
```