+++
title = "在Hugo中嵌入视频"
date = "2023-07-13T22:30:26+08:00"

#
# description is optional
#
# description = "An optional description for SEO. If not provided, an automatically created summary will be used."

tags = []
+++

### 嵌入Youtube视频
**1.在 /layouts/shortcodes/ 目录下创建youtube.html 并粘贴以下代码**
```
<div class="embed video-player">
  <iframe 
          class="youtube-player" 
          type="text/html" 
          width="640" 
          height="385"
          src="https://www.youtube.com/embed/{{ index .Params 0 }}?autoplay=1"
          style="
                 position: absolute; 
                 top: 0; 
                 left: 0; 
                 width: 100%; 
                 height: 100%; 
                 border:0;"
          allowfullscreen frameborder="0">
  </iframe>
</div>
```

**2.创建一个markdown 嵌入youtube视频参数为：**
```
##xxx为youtube视频链接watch?v=后面的数值
##编辑时将@删除
{@{< youtube xxx >}}

##自动播放
{@{< youtube id="xxx" autoplay="true" >}}
```

**效果:**
{{< youtube eIzqQJqyZr4 >}}


### 嵌入Bilibili视频
**1.在 /layouts/shortcodes/ 目录下创建bilibili.html 并粘贴以下代码**
```
<!DOCTYPE HTML>
<html>

  <head>
    <!-- style 样式 是为了让网页上的视频框按比例显示而非固定的大小 -->
    <style type="text/css">
      .aspect-ratio {
        position: relative;
        width: 100%;
        height: 0;
        padding-bottom: 75%;
      }

      .aspect-ratio iframe {
        position: absolute;
        width: 100%;
        height: 100%;
        left: 0;
        top: 0;
      }
    </style>
  </head>

  <body>
    <div class="aspect-ratio">
      <iframe
              src="https://player.bilibili.com/player.html?bvid={{.Get 0 }}&page={{ if .Get 1 }}{{.Get 1}}{{ else }}1&high_quality=1&danmaku=0{{end}}"
              scrolling="no" 
              border="0" 
              frameborder="no" 
              framespacing="0" 
              allowfullscreen="true"
              sandbox="allow-top-navigation allow-same-origin allow-forms allow-scripts"
              >
      </iframe>
      <!-- src 中的 &high_quality=1&danmaku=0 设定了高清程度并默认屏蔽弹幕 -->
      <!-- sandbox 阻止了点击视频中的按钮跳转到B站的行为 -->
    </div>
  </body>

</html>
```
**2.创建一个markdown 嵌入bilibili视频参数为：**
```
##xxx为bilibili视频链接video/后的数值
##编辑时将@删除
{@{< bilibili xxx >}} 

##指定集数
{@{< bilibili xxx 8 >}}
```

**效果:**
{{< bilibili BV13t411S77V >}} 