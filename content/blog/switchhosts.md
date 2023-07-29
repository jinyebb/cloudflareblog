+++
title = "中国地区提高Github访问速度"
date = "2023-07-29T20:23:00+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

**1.下载、安装SwitchHosts**

[下载地址](https://github.com/oldj/SwitchHosts/releases)

**2.SwitchHosts设置**

打开SwitchHosts，点击左上角"+" - 远程, Hosts标题自定义，URL输入https://raw.hellogithub.com/hosts 自动刷新1小时。

```
##MacOS下刷新hosts文件
sudo killall -HUP mDNSResponder
```