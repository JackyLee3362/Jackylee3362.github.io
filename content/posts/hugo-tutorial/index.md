---
title: 'Hugo 简易教程'
date: 2024-04-03T11:00:30+08:00
draft: true
author: JackyLee
tags: ["go"]
categories: ["教程"]
comments: true
---

## 配置文件

默认的配置文件

[sample-config.yml | hugo-PaperMod Wiki](https://github.com/adityatelange/hugo-PaperMod/wiki/Installation#sample-configyml)

## 优雅地添加图片

![崩坏星穹铁道](assets/1200px-star-rail.png)

[Hugo 博客插入图片的方法 | Cassius's Blog](https://www.yuweihung.com/posts/2021/hugo-blog-picture/)

## 添加 tag 和 category

参考如下文章

[Hugo框架中文文档 标签分类 - Andbible](https://www.andbible.com/post/hugo-content-management-taxonomies/#default-taxonomies)

```yaml
taxonomies:
  category: categories
  tag: tags
```

## 添加评论功能

### 方法一：原始的标签

最简单的是在 Giscus 配置好以后，获得 `<script>...</script>` 标签的内容，在 `themes/<theme_name>/layouts/partials/templates/comments.html` 里复制上

然后在 `footer.html` 的末尾添加如下代码

```html
{{- partial "comments.html" . -}}
```

该方法的问题

1. 在任何页面都会产生评论功能，比如主页，就不是很好看
2. 只能对特定主题生效，切换主题仍然需要重新配置

### 方法二：配置文件

todo

[Hugo 博客添加 Giscus 评论功能 | 云吱的小站](https://haoyep.com/posts/hugo-add-component/)

[giscus](https://giscus.app/zh-CN)

[Adding comments system to a Hugo site using Giscus](https://www.justinjbird.me/blog/2023/adding-comments-to-a-hugo-site-using-giscus/)

## 参考

[LoveIt](https://hugoloveit.com/zh-cn/)

[Cassius's Blog](https://www.yuweihung.com/)
