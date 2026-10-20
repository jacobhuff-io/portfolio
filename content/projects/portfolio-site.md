---
title: This Portfolio Site
date: 2026-10-20
summary: A static portfolio built with Hugo and the PaperMod theme, deployed to GitHub Pages with GitHub Actions.
tags: [hugo, github-pages, github-actions]
---

This site is built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

## How it works

- Content is written in Markdown under `content/`.
- PaperMod is pulled in as a Hugo Module, pinned in `go.mod`.
- Every push to `main` runs a GitHub Actions workflow that builds the site and deploys it to GitHub Pages.
- The site is served at a custom domain, with DNS managed at Porkbun.

[Source on GitHub](https://github.com/jacobhuff-io/portfolio)
