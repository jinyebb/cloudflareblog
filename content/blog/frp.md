+++
title = "搭建FRP内网穿透"
date = "2023-08-12T21:24:13+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

## FRP服务端设置

**1.FRP服务端一键安装**
```
wget https://raw.githubusercontent.com/MvsCode/frps-onekey/master/install-frps.sh -O ./install-frps.sh
chmod 700 ./install-frps.sh
./install-frps.sh install
```

**2.设置后台运行**
```
nohup ./frps -c frps.ini >/dev/null 2>&1 &
```

**FRPS常用命令**
```
开启FRPS：frps start
停止FRPS：frps stop
重启FRPS：frps restart
```

**防火墙端口放行**
```
##Debian或Ubuntu系统放行端口：
ufw allow 端口号
##CentOS系统放行端口：
firewall-cmd --zone=public --add-port=端口号/tcp --permanent
```

## FRP客户端设置

**1.下载对应系统FRPC客户端**

[https://github.com/fatedier/frp](https://github.com/fatedier/frp)

**2.修改frpc.ini配置文件**

```
[common]
server_addr = 服务器IP
server_port = 8021
token = xxxxxxxxxx

[服务名称]
type = tcp
local_ip = 127.0.0.1
local_port = 本地端口
remote_port = 远程端口
```

**3.启动配置文件**

```
./frpc -c ./frpc.ini
```