---
layout: post
title: "2、Jekyll：Windows下博客本地环境搭建流程"
# subtitle: "难度：Easy"
date: 2024-07-10 19:52:00
author: "WenXingming"
published: true
catalog: true
# header-img: "img/post-bg-2015.jpg"
# header-style: text
tags:
  - 博客搭建记录
---

在 [1、基于 Github Pages 的博客搭建流程记录](2024-07-08-001-Github-Pages-博客搭建流程记录.md) 中，已经搭建了我们自己的博客。但是每一次构建项目，都需要借助 Git 推送到 Github 帮助我们构建并在网站上发布。针对 Github 构建项目太慢，以及我们缺少一种本地化构建博客的方法来帮助我们进行可视化调试项目等问题，写此文章，本地搭建 jekyll 环境。

# 1、安装 Ruby 环境

**Ruby 是一门开源的动态编程语言**。Jekyll 是基于 Ruby 开发的，因此首先需要安装 Ruby 环境：[Ruby 环境安装](https://www.runoob.com/ruby/ruby-environment.html)，注意，安装时所有的勾都要选上（默认），特别是加入Ruby到环境变量这一选项。

## 1.1 安装 RubyGems（修改软件源）

**RubyGems是 Ruby 的一个包管理器**。这类似于 Ubuntu 下的 apt-get，Centos 的 yum，Python 的 pip。RubyGems 大约创建于2003年11月，从**Ruby 1.9版起成为Ruby标准库的一部分**（无需再手动安装），安装完 Ruby 后可以通过命令 `gem -v` 查看 gem。

**修改 RubyGems 的软件源**：由于国内网络原因（你懂的），导致 gem 很难做啊，现在教你一招：[RubyGems 介绍及修改软件源](https://www.runoob.com/ruby/ruby-rubygems.html)；或者直接通过以下命令：
```bash
gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
# 查看软件源
gem sources -l
```

# 2、安装 Jekyll

**Jekyll 是一个简单的博客形态的静态站点生产机器**。它有一个模版目录，其中包含原始文本格式的文档（如 Markdown），通过一个转换器和我们的 Liquid 渲染器转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。Jekyll 也可以运行在 GitHub Page 上，完全免费。

```bash
gem install jekyll
# 查看 Jekyll
jekyll -v
```

## 2.1 安装 jekyll-paginate（如果后续安装bundler，这里就不需手动安装。可选）

jekyll-paginate是一个用于分页的插件。在博客或者新闻网站中，文章或帖子的数量可能非常庞大，将它们全部显示在一个页面上会导致加载时间过长，影响用户体验。jekyll-paginate插件允许开发者将帖子分布在多个页面上，每页显示固定数量的帖子。

```bash
gem install jekyll-paginate
# 列出已安装的包，查看 jekyll-paginate
gem list --local
```

# 3、安装、使用 Bundler（额外）

上面两步其实已经足够了，但**为了方便管理项目的依赖，而不是手动通过 gem install 安装一个项目所需的许多个依赖**，我们需要 bundler。

**Bundler 是一个用于管理 Ruby 项目中 gem（包）依赖的工具**，它可以确保在不同机器和环境中，项目依赖的 gem 版本保持一致，从而避免因版本不一致而导致的问题。总的来说，Bundler 是 Ruby 项目依赖管理的关键工具，它通过提供一致的运行环境，**简化了 gem（包）的安装和管理过程**。

```bash
gem install bundler
# 查看 bundler
bundle -v
```

**bundle 的使用**：后续通过在**项目根目录下编写 Gemfile**，指定项目的 gem 依赖需求。在项目路径下执行命令 `bundle install` 即会使用自动使用 RubyGems 安装项目所需的所有依赖：

```bash
bundle install
# git add Gemfile Gemfile.lock
```

# 4、xx，启动！

```bash
# 执行 bundle install 安装项目文件 Gemfile 中指定的所有项目所需的 gem 依赖
bundle install # 不用每次都执行，应当是第一次运行项目时，执行一次即可
# 启动网站服务
jekyll serve 
jekyll serve --incremental # 有助于强制刷新缓存
# 访问地址：http://127.0.0.1:4000/ 或 localhost:4000
# bundle exec jekyll serve # 使用 bundle exec 可以确保 Jekyll 使用的是 Gemfile 中指定的 gem 版本，而不是全局安装的版本
```





