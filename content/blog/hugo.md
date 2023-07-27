+++
title = "搭建Hugo环境进行Github托管"
date = "2023-07-13T21:19:28+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

**1.搭建环境**

MacOS下需要安装Homebrew，其它操作系统访问[https://gohugo.io/installation](https://gohugo.io/installation/ "Title") 查询安装文档。

安装Homebrew
```
##安装时如弹出443错误,则需将终端配置网络代理
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

```
##终端代理配置格式
export https_proxy=http://127.0.0.1:7890
```
安装hugo并进行配置
```
##安装Hugo
brew install hugo
```

```
##创建blog
hugo new site blog
```

```
##初始化仓库
git init
```

```
##下载主题,也可访问https://themes.gohugo.io/ 获取其它主题
git submodule add https://github.com/jinyekey/hugo-y.git themes/hugo-y
```
使用VScode打开创建的blog文件夹，找到hogo.toml 设置主题
```
baseURL = '设置域名'
languageCode = 'en-us'
title = 'y Site'
theme = 'hugo-y'
```
运行hogo
```
##网站预览地址http://127.0.0.1:1313
hugo server -D
```
创建文章
```
hugo new blog/test.md
```

**2.托管到Github**

登陆Github-创建新存储库，存储库中点击Settings-Pages, Source项选择GitHub Actions点击browse all workflows 找到Hugo点击Configure，再点击Commit changes...提交更改。

使用Github Desktop将本地blog文件夹push到存储库

[Github Desktop下载](https://desktop.github.com/ "Title")

使用Github Pages提供的二级域名便可访问托管在Github上的Hogo网站


**3.托管到Cloudflare Pages**

登陆Cloudflare点击Workers和Pages，创建应用程序-Pages-连接到Git，选择之前创建的Github存储库-开始设置。

在 Pages 项目 >设置>环境变量中创建环境变量。将值设置为当前使用的Hugo版本。

```
##查看当前Hugo版本
hugo version
```

设置环境变量
* 变量名称:&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;HUGO_VERSION
* 值:&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;0.115.1