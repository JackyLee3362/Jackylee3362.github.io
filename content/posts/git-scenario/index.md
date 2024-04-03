---
title: 'Git 一些比较复杂的使用场景'
date: 2024-04-03T13:53:54+08:00
draft: true
author: JackyLee
tags: ["git"]
categories: ["场景"]
comments: true
---

## 前言

平常使用 `git add .` 或者 `git push|pull|clone` 等命令，已经无法满足各种奇怪的需求了，

在使用 Github 的时候，由于对远程分支和本地分支理解不够深刻，难免会出现各种问题

所以写篇文章记录下可能会遇到的各种场景

## 1 频繁遇到的场景

### 1.1 脏暂存

场景描述：

通常我会在 dev 分支上操作，然后细粒度地提交 commit，然后上传到 github 上形成一个 pull-request，然后 main 再接受，合并成一个

但是有时候会忘记切换分支（比如现在就是），直接在 main 上更改，在 vscode 的状态栏就会出现 `*`，此时想换到 `dev` 分支，该怎么做

答案 直接切换

### 1.2 提交树不为空

当提交树不为空时，可以切换分支吗

### 1.3 变基

## 2 偶尔遇到的场景

### 2.1

远程分支已删除，本地仍然保留远程分支

#### 如何解决

因为本地缓存了远程分支的信息，要删除本地缓存的已删除远程分支，可以使用以下 `git` 命令

```shell
git remote prune origin
```

### 场景 2

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
