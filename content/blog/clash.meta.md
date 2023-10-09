+++
title = "Clash For Windows切换Clash.Meta内核"
date = "2023-10-09T21:34:53+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

**Clash For Windows下载（根据自己的操作系统下载相应的版本）**

[下载地址](https://github.com/Fndroid/clash_for_windows_pkg/releases)

**Clash.Meta内核（根据自己的操作系统下载相应的版本）**

[下载地址](https://github.com/MetaCubeX/Clash.Meta/releases)

## Clash for windows切换Meta内核
**MacOS端切换内核**

打开Clash for windows报错，提示：已损坏，无法打开。 您应该将它移到废纸篓。

```
sudo spctl --master-disable
```

若还是无法运行，输入以下命令（命令后面空格），然后在程序中找到报错的程序拖动到终端框中，回车

```
sudo xattr -d com.apple.quarantine 
```

**将Clash.Meta内核拖至以下目录并更名clash-darwin**

M芯片路径

/Applications/Clash for Windows.app/Contents/Resources/static/files/darwin/arm64/clash-darwin

Intel芯片路径

/应用程序/Clash for Windows.app/Contents/Resources/static/files/darwin/x64/clash-darwin

**授权clash-darwin**
```
#输入以下命令（命令后面空格），clash-darwin拖动到终端框中
chmod +x 
```