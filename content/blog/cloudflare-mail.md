+++
title = "Cloudflare自定义域名邮箱"
date = "2023-07-27T19:15:30+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

**1.Cloudflare设置**

登录Cloudflare选择所需域名点击左侧电子邮件，选择添加记录并启用，在路由项目标地址处输入收发域名邮件的邮箱地址(gmail或hotmail均可)，自定义地址处输入自定义域名邮箱。

**2.Gmail设置**

登录[Google应用专用密码](https://myaccount.google.com/apppasswords)页面，选择:邮件-其他，输入应用自定义密码,选择生成。

进入Gmail-设置-查看所有设置-账号和导入-添加其他电子邮件地址，名称随意，电子邮件地址 处输入域名邮箱地址,SMTP服务器为smtp.gmail.com，端口587，用户名为gmail账号(去掉@gmail.com),密码为上面生成的自定义密码，点击添加账号，回到邮箱获取验证码进行验证，至此域名邮箱设置完成，在Gmail中即可用自定义域名邮件账号收发电子邮件。