---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }} # 发表日期（决定年份分组）
draft: true
authors: ["YOUR NAME"] # 作者列表（按论文顺序）
venue: "" # 会议 / 期刊名
doi: "" # 如 10.1145/123456.1234567（自动链接到 https://doi.org/...）
pdf: "" # PDF 链接，如 /files/papers/paper-title.pdf 或外部 URL
code: "" # 代码仓库链接
project: "" # 项目页面链接
abstract: "" # 摘要（也写入正文亦可）
tags: []
# bibtex = "@inproceedings{...}" # 可选：提供后在详情页自动展示 BibTeX
---

## Abstract

论文摘要。
