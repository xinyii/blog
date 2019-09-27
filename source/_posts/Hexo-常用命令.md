---
title: Hexo 常用命令
date: 2017-12-31 16:30:21
categories:
  - Hexo
tags:
  - Hexo
---

# 开始

- 安装 `npm install hexo-cli -g`
- 初始化 `hexo init blog`
- 进入目录 `cd blog`
- 安装依赖 `npm install`
- 启动服务 `hexo server`
- 查看帮助 `hexo help [command]`

<!-- more -->

# 工作流程

- 新建文章 `hexo n <title>` or `hexo new <title>`
- 新建草稿 `hexo n draft <title>` or `hexo new draft <title>`
- 发布草稿 `hexo p <title>` or `hexo publish <title>`
- 启动预览 `hexo s` or `hexo server`
- 预览草稿 `hexo s --draft`
- 生成页面 `hexo g` or `hexo generate`
- 部署推送 `hexo d` or `hexo deploy`