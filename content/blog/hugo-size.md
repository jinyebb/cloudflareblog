+++
title = "Hugo中调整Markdown字体大小"
date = "2024-09-09T19:00:26+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

在 layouts/shortcodes 目录下创建一个名为 fontsize.html 的文件，内容如下：
```
<span style="font-size: {{ .Get "size" }};">{{ .Inner }}</span>
```

然后在Markdown中这样使用：
```
{{< fontsize size="20px" >}}这是20像素的文本。{{< /fontsize >}}
```
