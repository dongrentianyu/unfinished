---
title: 关于本站
date: 2026-02-02
featuredImage: "/more/site.png"
featuredImagePreview: "/more/site.png"
---

{{< link href="https://unfinished-wenai.vercel.app/" content="本站网址" card=true >}}

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

## 防剧透设置

Fixit 主题中有加密文章的设计，我用来设计成防剧透。如果你不介意剧透，输入`1234`即可，如果你介意，请划过。但因为我写的很多文章都是跟具体的文化产品有关，比如某本书，电影或游戏，因而这确实是个难以言说的困扰。

{{% fixit-encryptor password="1234" message="密码是 1234" %}}

这是一段加密文本样式，输入 1234 即可打开。

{{% /fixit-encryptor %}}

## 本站导航

- 本站导航较为简单，只有两个导航栏
- more 下面包含的是我经常更新的主要页面
- classification 则是分类，这是总体上的分类，而非对文章本身的分类

## 分类说明

- 专栏通常都是合集，而合集还包含其它内容，比如 more 就是一个合集，且一些具有目录性质的也会做成合集
- 标签是所有文件都会有的，最常用的
- 专栏里的文章不会有`categories`字段

## 为什么没有友链界面却有推荐访问界面？

因为我是一个很喜欢看博客的人，而大多数博客都有友链，我会去看这些友链，而友链又有友链，我又会接着去点，换言之，这些网站可能都是友链之友链之友链了。而我本人也只是访问者，并不可能交到那么多朋友，我也不好厚着脸皮去要他们的网站信息。但我又同时想保存一下这些链接。我会经常访问我的网站，而存放这些链接也可以让我时不时去访问别人的网站。当然我知道大多数网站都有 RSS 选项，可以借助一些 RSS 阅读器来阅读文章，并不真的需要列出。但我认为博客样式也是很重要的部分，如果只是看文章内容，而少了博客样式，也是很可惜的事情。

## 本站架构

- 主要配置文件都放在`config/_default`文件夹中
- 主要内容放在`content`文件夹中
- 其中`content/columns/` 为专栏文件，其本质上与网站的 collections 合集功能是一样的，但我不想其呈现在 post 文章下面，也不方便管理，我单列出来了
- 其中`content/more`是关于本站的一些内容，会不断更新这些页面文章
- 其中`content/topic`则是单独自定义的，通常具有实例的事物会放在这个文件夹中
- 其它日常生活中则放在 post 文件夹中
