+++
title = "关于MacOS下appname.app已损的解决"
date = "2023-08-07T12:18:41+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

**1.开启任何来源**
```
sudo spctl --master-disable
```

**2.如以上方式无效,使用下面方法**
```
##打开Finder-应用程序-该app，将app图标拖至终端窗口
sudo xattr -r -d com.apple.quarantine /Applications/appname.app
```