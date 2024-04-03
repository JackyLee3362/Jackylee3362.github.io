---
title: 'Git 使用场景'
date: 2024-04-03T13:53:54+08:00
draft: true
author: JackyLee
tags: ["git"]
categories: ["场景"]
---

在使用 Github 的时候，由于对远程分支和本地分支理解不够深刻，难免会出现各种问题

现在记录一下遇到的各种场景

## 场景 1

远程分支已删除，本地仍然保留远程分支

### 如何解决

因为本地缓存了远程分支的信息，要删除本地缓存的已删除远程分支，可以使用以下 `git` 命令

```shell
git remote prune origin
```

## 场景 2

删除 `gitmodules`

```shell
# 取消关联
git submodule deinit -f <submodule-path>
# 删除 .gitmodules 文件
rm .gitmodules # linux
del .gitmodules
# 更新 Git 的索引以反映文件的删除
git rm --cached .gitmodules
# 提交
git commit -m "Remove .gitmodules file"
```

## 参考
