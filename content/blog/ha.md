+++
title = "Home Assistant技术文档"
date = "2023-07-13T22:34:23+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

## 目录
* [HACS无法安装midea ac lan的解决](#ha01)
* [Cloudflare tunnels绑定HA页面400: Bad Request的解决](#ha02)
* [Home Assistant通过手机来确定人员是否在家: Bad Request的解决](#ha03)


---

{{< anchor id="ha01" >}}

## HACS无法安装midea ac lan的解决

1.导航到/homeassistant/custom_components目录

```
cd /homeassistant/custom_components
```


2.从Releases页面下载midea_ac_lan.zip

```
wget https://github.com/georgezhao2010/midea_ac_lan/releases/download/v0.3.22/midea_ac_lan.zip -O midea_ac_lan.zip
```

3.解压缩midea_ac_lan.zip

```
unzip -d ./midea_ac_lan/ midea_ac_lan.zip
```

4.清理下载的midea_ac_lan.zip文件

```
rm midea_ac_lan.zip
```

5.重动Home Assistant

---

{{< anchor id="ha02" >}}

## Cloudflare tunnels绑定HA页面400: Bad Request的解决

Cloudflare tunnels添加本地Home Assistant服务，用域名访问内网的HA时，返回错误提示“400: Bad Request”

打开Home Assistant日志显示：

A request from a reverse proxy was received from 172.17.0.2, but your HTTP integration is not set-up for reverse proxies

这个日志表明Home Assistant检测到了来自反向代理的请求，但其HTTP 集成配置没有适当设置以处理这些请求。这通常与Home Assistant的http: 配置有关，特别是在处理代理和负载均衡器时。

以下是解决此问题的方法：

***1.配置http:部分***

在configuration.yaml中，需要正确配置http:部分以允许Home Assistant 识别反向代理的请求。添加或修改以下配置：  
（configuration.yaml文件在Home Assistant根目录下）
```
http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 172.17.0.0/24  # 允许反向代理的 IP 范围，或使用你的代理的 IP 地址或子网
```
* use_x_forwarded_for: true：启用对X-Forwarded-For 头部的支持，以便正确识别客户端的真实IP地址。  
* trusted_proxies:：列出你信任的反向代理的IP地址或IP 范围。如果你使用的是Docker，通常代理IP范围可能是 172.17.0.0/24（Docker默认网络）。

***2.重启Home Assistant***

保存配置文件后，需要重启 Home Assistant 使更改生效。你可以在 Home Assistant 界面中通过 Settings > System > Restart，或者使用命令行工具进行重启：
```
sudo systemctl restart home-assistant
```
或者，如果你使用 Docker：
```
docker restart homeassistant
```

***3.验证访问***

重启后，尝试通过你的域名访问Home Assistant，查看是否解决了400: Bad Request错误。

---


{{< anchor id="ha03" >}}

## Home Assistant通过手机来确定人员是否在家

原理是Home Assistant服务端ping局域网内的手机IP，ping的通表示在家，ping不通表示离家。

**1.添加ping集成**

* 在设置-设备与服务-添加集成中输入ping添加ping集成。

* 输入手机内网IP（将手机DHCP自动获取内网IP改为手动获取）

**2.配置ping集成**

进入该设备的实体列表，将刚添加的内网设备中的 已启用 与 可见 勾选。

**3.绑定设备和人员**

进入设置-人员，在 选择属于此人的设备 下添加刚才创建的ping集成设备。

**4.返回首页**

即可看到人员在家状态