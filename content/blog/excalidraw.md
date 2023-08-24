+++
title = "Docker搭建Excalidraw画图工具"
date = "2023-08-14T20:27:30+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

**1.创建配置文件**

```
##创建Excalidraw存放目录
mkdir -p /root/docker_data/excalidraw
cd /root/docker_data/excalidraw
```

在 /root/docker_data/excalidraw 目录下新建 docker-compose.yml

```
version: "3"

services:
  excalidraw:
    image: fanjunyang/jy-excalidraw # 默认使用latest的TAG，也就是我构建的最新镜像
    healthcheck:
      disable: true
    ports:
      - "8030:80"
    environment:
      BACKEND_V2_GET_URL: https://域名/excalidraw-storage-backend/api/v2/scenes/
      BACKEND_V2_POST_URL: https://域名/excalidraw-storage-backend/api/v2/scenes/
      LIBRARY_URL: https://libraries.excalidraw.com
      LIBRARY_BACKEND: https://us-central1-excalidraw-room-persistence.cloudfunctions.net/libraries
      SOCKET_SERVER_URL: https://域名/
      STORAGE_BACKEND: "https" # 协议是 https
      HTTP_STORAGE_BACKEND_URL: "https://域名/excalidraw-storage-backend/api/v2"

  excalidraw-storage-backend:
    image: kiliandeca/excalidraw-storage-backend
    ports:
      - "8031:8080"
    environment:
      STORAGE_URI: redis://redis:6379

  excalidraw-room:
    image: excalidraw/excalidraw-room
    ports:
      - "8032:80"

  redis:
    image: redis
    ports:
      - "6379:6379"
```

**2.运行yml文件**

```
##在/root/docker_data/excalidraw目录下，运行命令：
docker-compose up -d
```

**3.反向代理**

反向代理域名指向http://127.0.0.1:8030