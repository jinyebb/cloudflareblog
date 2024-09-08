+++
title = "在Hugo页面中目录跳转锚点的应用"
date = "2024-09-08T18:10:00+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

Hugo常规的锚点跳转Markdown语法为：

1.  
```
# 目录
* [目录一](#标题)
```

2.  
```
## 标题
//跳转目的地
```


而锚点跳转到页面指定位置，并非某段文章标题时，可以使用Hugo Shortcodes，操作如下：

***1.创建Shortcode文件***

Hugo项目的根目录下，找到或创建一个layouts/shortcodes 目录。

***2.编辑Shortcode文件***

编辑或创建anchor.html文件，并添加如下内容：
```
<a id="{{ .Get "id" }}"></a>
```
Shortcode会生成一个带有指定ID的锚点

***3.在Markdown文件中插入Shortcode***

在Markdown文件中，使用Shortcode来插入跳转到目的地的锚点：
```
{{< anchor id%"display" >}}
// 该段语法中%替换为=
```
这行代码会在生成的HTML中插入一个带有ID:display的锚点。

***4.链接到锚点***

在Markdown文件中的其他位置创建链接，指向这个锚点：
```
[跳转到锚点](#display)
```

***5.完整示例***

```
## 目录

- [跳转到锚点](#display)

## 显示部分

{{< anchor id="display" >}}
这里是显示部分的内容。
```


22

```
{{< anchor id%"display" >}}
// 该段语法中%替换为=
```