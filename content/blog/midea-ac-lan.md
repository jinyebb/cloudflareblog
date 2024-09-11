+++
title = "HACS无法安装midea ac lan的解决方法"
date = "2024-09-11T20:16:16+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

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