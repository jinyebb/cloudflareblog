+++
title = "Docker可视化面板Portainer安装"
date = "2023-07-13T22:37:48+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

```
##拉取Portainer镜像
docker pull portainer/portainer
```

```
##查看镜像
docker images
```

```
##安装Portainer镜像,Web端口为9000
docker run -d -p 9000:9000 --name=sun_portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
```

```
##Portainer界面地址
http://127.0.0.1:9000
```