---
title: 关于本站
date: 2026-02-02
lastmod: 2026-02-06
featuredImage: "/more/site.png"
featuredImagePreview: "/more/site.png"
---

## 本站简介

本站名称来源于 X JAPAN 的《unfinished》。域名后缀 WENAI 是我之前使用的。

{{< aplayer fixed=false mini=false autoplay=false theme="#b7daff" loop="all" order="list" preload="auto" volume=0.7 mutex=true lrcType=3 listFolded=false listMaxHeight="" storageName="aplayer-setting" >}}
{{< audio name="Unfinished" artist="X JAPAN - BALLAD COLLECTION"
url="https://files.catbox.moe/4kdy06.flac"
cover="https://p3.music.126.net/hMvHZtjBqCXLSpMu5OgqOw==/869713697571074.jpg"
lrc="/music/unfinished.lrc" />}}
{{< /aplayer >}}

本站采用 Hugo 和 Fixit 主题，使用 Vercel 进行部署，未来会考虑购买域名。

本站包含博客，知识库，文档，专栏等，内容上涉及书籍，电影，动画，游戏等，也有关于学习方法，笔记软件等相关文章。总之，我希望写下我值得去写的一切内容。

本站不是知识管理的项目，不会把简短的笔记放在这里。

https://unfinished-wenai.vercel.app/

## 本站导航

- 本站导航较为简单，只有两个导航栏
- more 下面包含的是我经常更新的主要页面
- classification 则是分类，这是总体上的分类，而非对文章本身的分类

## 本站架构

- 主要配置文件都放在`config/_default`文件夹中
- 主要内容放在`content`文件夹中
- 其中`content/columns/` 为专栏文件，其本质上与网站的 collections 合集功能是一样的，但我不想其呈现在 post 文章下面，也不方便管理，我单列出来了
- 其中`content/more`是关于本站的一些内容，会不断更新这些页面文章
- 其中`content/topic`则是单独自定义的，通常具有实例的事物会放在这个文件夹中
- 其它日常生活中则放在 post 文件夹中
