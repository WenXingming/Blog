---
layout: post
title: "关于Github Pages"
subtitle: "Github Pages的简要介绍和使用"
date: 2024-07-12 23:34:12
author: "WenXingming"
published: true
catalog: true
# header-img: "{{baseurl}}/img/xxx"
tags: [Github]给[官方手册](https://docs.github.com/zh/pages
---


关于 Github Pages 的更多内容，请查看：[官方手册](https://docs.github.com/zh/pages)。再多的博客，也比不上读一遍手册！

# 关于 Github Pages

为什么使用 Github Pages？①免费：白嫖 Github 的服务器；②方便：和 Github 深度集成，对于发布一些静态网站来说很方便（特别是可以使用 Github Actions 帮助我们自动构建、并直接发布到 Github Pages）

什么是 Github Pages？**GitHub Pages** 是一个**静态站点**托管服务，它**直接从 GitHub 上的仓库获取 HTML、CSS 和 JavaScript 文件**，（可选）通过**构建**过程运行文件，然后**发布**网站。

怎么使用 Github Pages？①我们可以直接将（本地）构建好后的静态网站推送到我们的仓库里，并通过 Github Pages 发布网站；②通过 Github 帮助将源码构建为静态网站（这也是 Github Pages 默认执行的），并通过 Github Pages 发布网站。通常，我们不希望频繁地本地构建自己的网站（懒、耗费时间等），所以选择第②种方式；

# Overview

在使用 Github Pages 后，Github 会**默认自动帮助构建**生成静态文件（即采用第②种方式。注意Github 提供的默认静态站点生成器是 Jekyll）。

如果不想使用 Jekyll，可以使用 **GitHub Actions** 自定义工作流过程，来使用其他静态站点生成器等来构建和发布站点。

如果不想使用 Github 提供的默认静态站点生成器 Jekyll，也不想使用自定义 Github Actions 工作流（可以自定义使用其他的静态站点生成器），即不通过 Github 来帮助构建生成静态文件，那么只能直接上传静态网站的文件到 Github 仓库。此时，需要通过在发布源的根目录中创建一个名为 .nojekyll 的空文件来禁用 Jekyll 生成过程（因为默认是启用 Jekyll 构建仓库的），然后在本地生成静态站点文件并上传到 GitHub 仓库。

总之：**（Ⅰ）如果不使用 Github 帮助构建**。那么只能直接上传静态网站的文件到 Github 仓库，此时需要通过在发布源（一般为仓库本身）的根目录中创建一个名为 .nojekyll 的空文件来禁用 Jekyll 生成过程；**（Ⅱ）**使用 Github 帮助构建。**（Ⅱ-1）Github 默认使用静态站点生成器 Jekyll 帮助构建仓库**（在将更改推送到设置的分支时触发），然后发布到 Github Pages；**（Ⅱ-2）或者自定义 Github Actions 工作流**（自定义触发器），在工作流中自定义构建过程、并发布到 Github Pages；

----

在我的个人博客中，使用的是 Jekyll 静态站点生成器，所以我可以创建一个 Github Page，并直接使用Github 默认执行的 Jekyll 构建过程来生成自己的静态博客站点，完全**不需要自定义 Github Actions**。在此过程中，如果还有什么需要更改的话，也就是设置一下 Github Pages 的发布源是 master分支，还是自己定义一个新的分支（一般命名为 gh-pages）专门存放构建生成的静态网站文件，然后 Github Pages 将使用这个新的分支的文件来发布网站。