---
title: hugo 和 fixit 备忘录
summary: 记下一些备忘
date: 2026-02-07
---

## 借用 cascade 进行批量设置

比如我经常会写一些文章，放进同一个文件夹里，方便管理。那我就可以在那个文件夹的里面写上一个`_index.md`，内容如下。其中在 cascade 中设置 collections，然后 hugo 就会默认这个文件夹下面所有 md 文件都具有此字段。

当然这个可以被 md 文件中自带的 collections 覆盖。

包括下面的 url，都可以统一设置成某个特定链接，也可以加上日期之类的。

```
---
title: 年终总结
date: 2026-02-06
subtitle: "每年总结一点，一生就总结这些每年总结好了"
url: "/columns/years-end/"
collections:
cascade:
  params:
    type: posts
    collections: 年终总结
  url: "/columns/years-end/:title" # 自定义路径
description:
---
```

## 常用 shorts code

```
> The quick brown fox jumps over the lazy dog.
{.blockquote-center}
```

```
{{% fixit-encryptor "1212" "密码是 1212" %}}
`fixit-encryptor` shortcode 在版本 {{< version 0.2.15 >}} 得到支持。
{{% /fixit-encryptor %}}
Or
{{% fixit-encryptor password="1212" message="密码是 1212" %}}
`fixit-encryptor` shortcode 在版本 {{< version 0.2.15 >}} 得到支持。
{{% /fixit-encryptor %}}
```
