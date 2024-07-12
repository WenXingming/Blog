---
layout: post
title: "01 关于Github Pages"
subtitle: "Github Pages的介绍和使用"
date: 2024-07-12 23:34:12
author: "WenXingming"
published: true
catalog: true
# header-img: "{{baseurl}}/img/xxx"
tags: [Github]
---

[官方手册](https://docs.github.com/zh/pages)

# 为什么使用 Github Pages

1. 免费。白嫖 Github 的服务器
2. 方便。和 Github 集成，对于发布一些静态网站来说很方便

# 什么是 Github Pages

[GitHub Pages](https://docs.github.com/zh/pages)，是一个**静态站点**托管服务，它**直接从 GitHub 上的仓库获取 HTML、CSS 和 JavaScript 文件**，（可选）通过**构建**过程运行文件，然后**发布**网站。

[GitHub Pages 站点的类型有三种](https://docs.github.com/zh/pages/getting-started-with-github-pages/about-github-pages#github-pages-%E7%AB%99%E7%82%B9%E7%9A%84%E7%B1%BB%E5%9E%8B)，只能为 GitHub 上的每个帐户创建一个用户或组织站点。 项目站点（无论是组织还是个人帐户拥有）没有限制。

# Github Pages 静态文件的来源

GitHub Pages 会发布我们推送到仓库的任何静态文件。静态文件的来源：
- 自己本地构建好后上传；
- 通过 Github 帮助构建（主要学习这一种）生成静态站点的文件；

# Github 会自动帮助构建生成静态文件

①在将更改推送到特定分支时**自动帮助构建、发布站点**；②可以**编写 GitHub Actions 工作流来控制构建、发布站点**。

- **在将更改推送到特定分支时自动构建、发布站点（默认使用 Jekyll 来 build 仓库）**。如果不需要对站点的生成过程进行任何控制（即使用 Jekyll 构建仓库生成静态站点），则建议使用这种方法。在这种方法中，可以指定要用作发布源的**分支和文件夹**。 源分支可以是存储库中的任何分支，源文件夹可以是源分支上的存储库根目录 (/)，也可以是源分支上的 /docs 文件夹。
- **编写 GitHub Actions 工作流来发布站点**。如果想使用 **Jekyll 以外**（GitHub原生支持 Jekyll 静态站点生成器）的生成过程，或者不想**使用专用分支来保存已编译的静态文件**，则建议编写 GitHub Actions 工作流来发布站点。

# 关于静态站点生成器

在使用“在将更改推送到特定分支时自动构建、发布站点”时，Github 的默认支持的静态站点生成器是 Jekyll。如果不使用 Jekyll，可以使用 GitHub Actions 自定义工作流过程，来使用其他静态站点生成器等来构建和发布站点（GitHub 为多个静态站点生成器都提供了入门工作流）。

如果不想使用 Github 提供的默认静态站点生成器 Jekyll，也不想使用其他的静态站点生成器和自定义 Github Actions 工作流，那么只能直接上传静态网站的文件到 Github 仓库。此时，需要通过在发布源的根目录中创建一个名为 .nojekyll 的空文件来禁用 Jekyll 生成过程，然后在本地生成静态站点文件并上传到 GitHub 仓库。

