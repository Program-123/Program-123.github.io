---
title: "How This Website Is Built"
date: 2026-07-02
draft: false
description: "A placeholder post about the stack behind this site: Hugo, Blowfish, GitHub Pages and GitHub Actions."
tags: ["Hugo", "Static Site", "DevOps"]
categories: ["Engineering"]
---

> ⚠️ **Placeholder post** — 建站技术栈说明的占位文章。

This site is fully static — no backend, no database, no SPA framework. The
stack:

| Layer    | Tool                             |
| -------- | -------------------------------- |
| SSG      | Hugo (Extended)                  |
| Theme    | Blowfish                         |
| Hosting  | GitHub Pages                     |
| CI / CD  | GitHub Actions                   |
| Content  | Markdown                         |

## Why a static site?

Static sites are fast, cheap to host, easy to version, and hard to break.
For a personal homepage with a portfolio, publications, and a blog, that is
all you need.

## Deployment flow

Every `git push` to `main` triggers a GitHub Actions workflow that builds the
site with `hugo --minify` and publishes the `public/` directory to GitHub
Pages.
