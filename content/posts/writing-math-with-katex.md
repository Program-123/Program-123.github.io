---
title: "Writing Math with KaTeX"
date: 2026-08-14
draft: false
description: "A placeholder post demonstrating LaTeX math rendering via KaTeX in Blowfish."
tags: ["Tutorial", "LaTeX"]
categories: ["Notes"]
math: true
---

{{< katex >}}

> ⚠️ **Placeholder post** — 数学公式演示文章。
> 本页 front matter 中的 `math: true`（加上文首的 `{{</* katex */>}}` 标记）启用了 KaTeX。

Inline math such as $e^{i\pi} + 1 = 0$ renders inside a sentence, and the
normalization formula $\mathbf{x}' = \frac{\mathbf{x} - \mu}{\sigma}$ works
too.

Block math is written with `$$ ... $$`:

$$
\mathcal{L}(\theta) = -\frac{1}{N} \sum_{i=1}^{N} \sum_{c=1}^{C}
y_{i,c} \log \hat{y}_{i,c}(\theta)
$$

The attention mechanism from the Transformer architecture:

$$
\mathrm{Attention}(Q, K, V) = \mathrm{softmax}\!\left(\frac{QK^{\top}}{\sqrt{d_k}}\right)V
$$
