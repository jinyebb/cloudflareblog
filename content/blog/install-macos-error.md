+++
title = "安装MacOS时进度条卡死的解决"
date = "2023-08-10T20:46:17+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

**原因:**

因为打印机程序最低系统要求为Catalina 10.15，随即升级到该系统后发现一个难以接受的问题:断开电源线和合上笔记本都会出现系统自动关机的症状，随即又更新到Big Sur 11想试试这个问题是否会得到解决，在屏幕显示安装剩余1分钟时进度条卡死，试过重启试过option+command+r恢复出厂设置重新安装仍然卡死在"剩余1分钟"，折腾一天最后找到解决方法

**解决方式:**

开机状态下断开电源线，同时按下option+command+r+p不要松开按键，经过5次重启后松开手指，再重新安装一遍，进度条将不会再卡死，

安装完成进入系统后，风扇可能会一直狂转，解决方法如下:

1.将Mac关机，按住Control+Option+Shift 7秒钟，然后在不松开按键情况下按住电源按键，Mac将会关机。

2.继续按住全部四个按键7秒钟，然后松开这些按键。

3.等待几秒钟，然后按下电源按钮以将Mac开机。