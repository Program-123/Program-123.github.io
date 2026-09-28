---
title: "这个网站是如何搭建的"
date: 2026-07-02
draft: false
description: "占位文章：介绍本站技术栈——Hugo、Blowfish、GitHub Pages 与 GitHub Actions。"
tags: ["Hugo", "静态网站", "DevOps"]
categories: ["工程"]
---

> ⚠️ **占位文章** —— 建站技术栈说明的占位文章。

本站是完全静态的——没有后端、没有数据库、没有 SPA 框架。技术栈如下：

| 层级     | 工具              |
| -------- | ----------------- |
| 静态生成 | Hugo（Extended）  |
| 主题     | Blowfish          |
| 托管     | GitHub Pages      |
| 持续部署 | GitHub Actions    |
| 内容     | Markdown          |

## 为什么选择静态网站？

静态网站速度快、托管成本低、易于版本管理、也不容易出故障。
对于一个包含作品集、论文列表和博客的个人主页来说，这些已经完全够用。

## 部署流程

每次向 `main` 分支 `git push` 都会触发 GitHub Actions 工作流，
用 `hugo --minify` 构建站点并把 `public/` 目录发布到 GitHub Pages。
