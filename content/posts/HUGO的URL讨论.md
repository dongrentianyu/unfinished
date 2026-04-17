---
title: HUGO的URL讨论
date: 2026-04-17
lastmod: 2026-04-17
subtitle:
tags:
  - HUGO
categories:
featuredImagePreview:
featuredImage:
draft: false
imageLink:
---

<!--more-->

我一开始没意识到这个问题，但当我一直纠结taxonomy 的配置应该怎么处理时，我后面终于搞清楚了。

## 两套界面

问题其实非常简单，HUGO有两套页面。一套是section，类似于归档页面那样，按时间排序呈现内容，路径是文件夹URL。另一套是taxonomy，由分类方法生成URL。官方推荐是这种方式书写，左边是单数，右边是复数。

这两套逻辑，以section为主要，产生冲突时也是渲染section。

```toml
[taxonomies]
  model = "models"      # 左边 model（单数），右边 models（复数）
  # 或者
  category = "categories"
  tag = "tags"
```

但在实际过程中，左边是复数也可以，右边也是单数也可以，左右两边都是单数或复数也可以。

```toml
[taxonomies]
  models = "models"     # 左边复数 = 右边复数
```

```toml
[taxonomies]
  model = "model"       # 完全用单数（官方也支持，如果你永远只用单个值）
```

为什么会这样呢？很简单，因为这不是强制性要求的，而更像是某种约定。因为背后是在读取字符串的。

因而实际上如果想做真正的区分的话，采用不同词语应该是更加正确的。

```toml
[taxonomies]
  model = "model-types"   # 或 "model-tags"、"arts" 等
```

这样就不会有任何问题。生成的路径如下：

```plain/text
# 假设你的文件夹结构是content/models/art/test.md
localhost:1313/models/art/test/ # 这是在生成实际的url
localhost:1313/models/art/    # 这是在生成section
localhost:1313/model-types/art/    # 这是在生成taxonomy的url，这个界面就等同于categories界面，同样可以单独进行配置 
```

## MarkDown字段属性

这里面还夹杂了另外一个问题，正常来说上面taxonomy配置中，左边是md文件中的字段名，而右边是taxonomy的分类法。

```yaml
---
title: test
model: art # 正常来说应该左边字段名，右边为具体的值，但这样写只能在生成下面的url
---
```

```toml
localhost:1313/model/art/test # 这个url是存在的，且可访问的
localhost:1313/models/art # 这个url也存在，但没有内容
localhost:1313/model-types/art # 这个url不存在，或空内容无法访问
```

所以在实际书写md属性时，应该采用右边的值，而不是左边的。这样才能生成相对应的taxonomy界面。不然url文件又会混乱。

混乱是指这个文件存在，页面存在，但你不清楚URL是什么。

### 单值属性书写

这里还有个话题，正常来说taxonomy中规定的属性，应该写成数组。但实际上，如果只是单值，那写成标量字符串也是完全没有问题的，两者底层是一致的。HUGO这一点竟然都没有做强约束，不知道是考虑TOML与YAML两者存放格式的区别还是什么。

```yaml
---
title: test
model: art # 合法
model: ["art"] # 合法，两者表达方式是一致的
---
```

## 最终处理

最终我的处理方式是全都保持一致，在正常生成section的界面中，使用layout属性，修改成taxonomy界面。

```toml
model = "models" #taxonomies.toml 文件中这样设置
```

文件夹路径列表如下，可查看GitHub仓库进一步详细查看 

```file-tree
- name: content
  type: dir
  children:
    - name: posts
      type: dir
      children:
        - name: test.md
          type: file
    - name: models
      type: dir
      children:
        - name: _index.md
          type: file
        - name: art
          type: dir
          children:
            - name: _index.md
              type: file
            - name: one.md
              type: file
```

在 `content/models/_index.md` 中这样写，强制使用 `layout` 属性将原来的section界面改成taxonomy界面。又因为两者路径一致，所以不会有冲突

```yaml
---
title: 大模型
date: 2026-04-14
layout: "taxonomy"
titleIcon: fa-solid fa-brush
portals: port
---
```

在`content/models/art/_index.md` 则这样写，使用cascade，进行统一设置单值，不需要在里面每个文件都这样处理。且必须要有models的空值。同时这里也可以使用其它分类的属性值，比`portals: model` 就使此文件可以在其它分类列表中展示了。

```yaml
---
title: 艺术
date: 2026-04-14
models: #这里要留空，不然下面的cascade会把此_index.md文件也放进去
portals: model
cascade:
  params:
    type: posts
    model: ["art"]
description:
---
```