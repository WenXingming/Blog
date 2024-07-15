---
layout: post
title: "关于Github Pages"
subtitle: "Github Pages的简要介绍和使用"
date: 2024-07-12 23:34:12
author: "WenXingming"
published: true
catalog: true
# header-img: "{{baseurl}}/img/xxx"
tags: [Github]
---


关于 Github Pages 的更多内容，请查看：[官方手册](https://docs.github.com/zh/pages)。再多的博客，也比不上读一遍手册！

# 关于 Github Pages

为什么使用 Github Pages？①免费：白嫖 Github 的服务器；②方便：和 Github 深度集成，对于发布一些静态网站来说很方便（特别是可以使用 Github Actions 帮助我们自动构建、并直接发布到 Github Pages）

什么是 Github Pages？**GitHub Pages** 是一个**静态站点**托管服务，它**直接从 GitHub 上的仓库获取 HTML、CSS 和 JavaScript 文件**，（可选）通过**构建**过程运行文件，然后**发布**网站。

怎么使用 Github Pages？①我们可以直接将（本地）构建好后的静态网站推送到我们的仓库里，并通过 Github Pages 发布网站；②通过 Github 帮助将源码构建为静态网站（这也是 Github Pages 默认执行的），并通过 Github Pages 发布网站。通常，我们不希望频繁地本地构建自己的网站（搭建环境麻烦、懒、耗费时间等），所以选择第②种方式，让 Github 自动帮助我们构建、发布；

# Source 的选择

新建一个仓库，打开 Settings 界面，左侧边栏选择 Pages，查看 Build and deployment 选项，选择 Source 后，就自动可以使用 Github Pages 了。首先，我们可以看到 Source 有两个选项：Github Actions || Deploy from a branch，接下来将详细解释这两种选择。

**Deploy from a branch**：顾名思义，将 Source 选择为此时，Github 会自动使用仓库中你选中的分支的内容，并使用 Jekyll（Github 提供的默认静态站点生成器是 Jekyll）帮助构建生成静态文件，然后自动发布到 Github Pages。如果不想 Github 使用默认静态站点生成器 Jekyll 对项目进行构建，则需要通过在发布源的根目录中创建一个名为 .nojekyll 的空文件来禁用 Jekyll 构建生成过程。

**Github Actions**：将 Source 选择为 Github Actions 是**自定义**构建、发布过程的最佳选择。在此过程中，我们需要学习编写 .yml 文件（需要在项目根目录下的 .github/workflows 目录中定义该文件，Github 识别到便会根据此文件自动执行 Actions）控制 Github Actions 的具体动作、行为。关于自定义 Github Actions 工作流：请参照 [通过 GitHub Pages 使用自定义工作流](https://docs.github.com/zh/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages)。需要提醒的是，编写 .yml 文件的过程中，很多时候都可以使用已经被广泛使用的开源 actions 来帮助我们完成一些普遍的功能。我们可以在 Github Actions 中直接将构建得到的静态文件发布到 Github Pages（通常使用开源的 actions 帮助完成）。

**Deploy from a branch、Actions 结合使用**：在 Github Pages 界面选择 Source 为 **Deploy from a branch** 时，也可以通过编写 .yml 文件，使用 Github Actions帮助我们构建项目，可以将得到的静态文件存储到我们自己仓库的分支（通常使用开源的 actions 帮助完成，且通常发布在 gh-pages 分支）。在此种情况下，需要设置 Source 为 **gh-pages分支**，这样便可以将 gh-pages 分支中的静态文件发布到 Github Pages（注：Github 会默认使用静态站点生成器 Jekyll 帮助构建仓库，而开源 actions 帮助将构建得到的静态文件添加到仓库 gh-pages 分支时，一般可能会自动添加一个名为 .nojekyll 的空文件来禁用 Jekyll 生成过程，这也是我们想要的）。

如果不想使用自定义 Github Actions 工作流（其中可以自定义使用其他的静态站点生成器），也不想使用 Github 提供的默认静态站点生成器 Jekyll，即不通过 Github 来帮助构建生成静态文件，那么可以直接将本地构建好的静态网站文件上传到 Github 仓库。此时，需要在仓库的 Settings 页面设置 Pages，将 Source 选择为 "Deploy from a branch"，并在发布源分支的根目录中创建一个名为 .nojekyll 的空文件来禁用 Jekyll 生成过程（因为 Github 默认是会启用 Jekyll 构建仓库的）。这种方式类似于上面提到的使用 Github Actions 将构建得到的静态文件存储到仓库 gh-pages 分支的行为，只不过构建过程是我们自己本地完成的而不是 Github Actions 帮助完成的。

Github Pages 的发布源一共只有 Github Actions || Deploy from a branch 这两种选择。其中当选择后者时，Github 将默认使用 Jekyll 构建仓库分支中的内容，而如果分支中的内容已经是静态文件了（无论是通过 Github Actions 构建后推送到分支的，还是自己本地构建好上传的），我们便不需要 Jekyll 帮助构建，此时可以在分支的根目录中创建一个名为 .nojekyll 的空文件来禁用 Jekyll 生成过程。

-------

在我的个人博客中，使用的是 Jekyll 静态站点生成器，所以我可以创建一个仓库并使用 Github Pages，直接使用 Github 默认执行的 Jekyll 构建过程来生成自己的静态博客站点，完全不需要自定义 Github Actions。当然，我也可以使用自定义 Github Actions 构建、直接发布到 Github Pages；或者使用自定义 Github Actions 构建、推送到 gh-pages 分支，在这种情况下，我需要在在仓库的 Settings 页面设置 Pages，将 Source 选择为 "Deploy from a branch" 的 gh-pages 分支（源分支的根目录中创建一个名为 .nojekyll 的空文件来禁用 Jekyll 生成过程，这通常可能由 .yml 中使用的 actions 自动完成）。