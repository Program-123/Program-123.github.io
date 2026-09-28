---
title: "用 KaTeX 书写数学公式"
date: 2026-08-14
draft: false
description: "占位文章：演示 Blowfish 中通过 KaTeX 渲染 LaTeX 数学公式。"
tags: ["教程", "LaTeX"]
categories: ["笔记"]
math: true
---

{{< katex >}}

> ⚠️ **占位文章** —— 数学公式演示。
> 本页 front matter 中的 `math: true`（加上文首的 `{{</* katex */>}}` 标记）启用了 KaTeX。

行内公式如 $e^{i\pi} + 1 = 0$ 可以出现在句子中间，归一化公式
$\mathbf{x}' = \frac{\mathbf{x} - \mu}{\sigma}$ 也可以正常渲染。

块级公式用 `$$ ... $$` 书写：

$$
\mathcal{L}(\theta) = -\frac{1}{N} \sum_{i=1}^{N} \sum_{c=1}^{C}
y_{i,c} \log \hat{y}_{i,c}(\theta)
$$

Transformer 架构中的注意力机制：

$$
\mathrm{Attention}(Q, K, V) = \mathrm{softmax}\!\left(\frac{QK^{\top}}{\sqrt{d_k}}\right)V
$$
