+++
title = "X-Ui安装"
date = "2023-07-13T22:36:26+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

**aaPanel安装脚本**
<br />

[点击](https://www.aapanel.com/new/download.html#install)

**X-ui一键脚本**
```
bash <(curl -Ls https://raw.githubusercontent.com/FranzKafkaYu/x-ui/master/install.sh)
```
```
##Debian/Ubuntu 系统执行以下命令：
apt update -y
apt install -y curl
apt install -y socat
```

```
##CentOS 系统执行以下命令：
yum update -y
yum install -y curl
yum install -y socat
```

```
##放行端口
iptables -I INPUT -p tcp --dport 443 -j ACCEPT
```