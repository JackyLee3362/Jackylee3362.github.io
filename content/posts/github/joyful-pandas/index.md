---
title: Github开源项目 Joyful Pandas 阅读笔记
date: 2024-04-06T00:52:55+08:00
draft: true
author: JackyLee
tags: [python]
categories: [github, 教程]
comment: true
---

最近准备复现一些实验，每次都要重新学 Pandas 的一些语法，刚好看到了这个仓库

[仓库地址](https://github.com/datawhalechina/joyful-pandas)

## 仓库介绍

作者是 [Datawhale](https://github.com/datawhalechina)，一个专注于数据科学与 AI 领域的开源组织（有 100+ 个仓库，厉害！

2020.1.20 建立仓库，初始化 README.md

```markdown
# Joyful-Pandas

A Complete Guide for Pandas Learners
```

5 年期间不断更新，最近一次是在 2024.10.17，更新了英文的介绍

## 代码方面

代码写的非常优雅，不过因为我的 Pandas 版本比较高，所以部分函数失效，比如 `DataFrame` 的 `mad` 函数，在 `pandas` 的 `2.0` 版本之后就废弃了

或者说使用 `any(1)` 或者 `all(1)` 时，新版的 Pandas 需要显示地指定形参名，所以建议改为 `any(axis=1)` 和 `all(axis=1)`

然后就是格式化稍微有点问题（不影响代码运行）

## 评价

总体来说是个非常好的教程仓库

## 参考

[datawhalechina/joyful-pandas: pandas 中文教程](https://github.com/datawhalechina/joyful-pandas)
