---
title: Hugo 工作流
date: 2024-04-03T17:20:20+08:00
draft: true
author: JackyLee
tags: [hugo, go]
categories: [工作流]
comments: true
---

## Huge 发布工作流

### 第一步：生成文章模板

```shell
hugo new --kind <archetypes> <path/to/post>/index.md
# 例如
hugo new --kind post path/to/post/index.md
```

### 第二步：修改 tags 和 categories

```yaml
tags: []
categories: []
```

### 第三步：创作

写文章

### 第四步：提交
