+++
title = "Markdown超链接在新窗口中打开"
date = "2023-07-13T22:33:07+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

**新建目录layouts/_default/_markup/ 并创建render-link.html**

***##粘贴以下参数***

```
<a href="{{ .Destination | safeURL }}"{{ with .Title}} title="{{ . }}"{{ end }}{{ if strings.HasPrefix .Destination "http" }} target="_blank" rel="noopener"{{ end }}>{{ .Text | safeHTML }}</a>
```

```
[链接](https://www.github.com "Title")
```