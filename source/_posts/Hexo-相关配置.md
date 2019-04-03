---
title: Hexo 相关配置
date: 2017-12-31 17:26:50
categories:
	- Hexo
tags:
	- Hexo
---

#### 配置

当前版本 `hexo 3.2.2`
hexo站点配置文件 `_config.yml`

<!-- more -->

```yml
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: # 博客标题
subtitle: # 博客子标题
description: # 博客简介
author: # 作者名
language: zh-Hans # 语言
timezone: Asia/Shanghai # 时区

# URL
## If your site is put in a subdirectory, 
## set url as 'http://yoursite.com/child' and root as '/child/'
url: # 网站url，例：http://xinyiii.ml
root: # 网站根目录，例：/
permalink: # 文章链接格式，例：:year/:month/:day/:title/
permalink_defaults: # 文章链接格式默认值

# Directory
source_dir: source # 资源目录
public_dir: public # 生成目录
tag_dir: tags # 标签目录
archive_dir: archives # 归档目录
category_dir: categories # 分类目录
code_dir: downloads/code # 代码目录
i18n_dir: :lang # 国际化目录
skip_render: # 跳过渲染目录

# Writing
new_post_name: :title.md # 新建文章文件名格式
default_layout: post # 新建文章默认
titlecase: false # 自动标题大小写
external_link: true # 打开链接到新标签
filename_case: 0 # 将文件名转换为1小写; 2大写
render_drafts: false # 显示草稿
post_asset_folder: false # 启用asset文件夹
relative_link: false # 链接相对地址
future: true # 显示未来的帖子
highlight: # 代码高亮设置
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:

# Category & Tag
default_category: uncategorized # 默认不分类
category_map:
tag_map:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10 # 每页显示文章数
pagination_dir: page

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next # 主题设置

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy: # 部署远程仓库设置
  type: git
  repo: 
    github: git@github.com:xxx/xxx.git,gh-pages # github仓库地址
    coding: git@git.coding.net:xxx/xxx.git,coding-pages # coding仓库地址

# 自动生成sitemap
baidusitemap:
path: baidusitemap.xml

```

#### 参考

[Hexo官方配置说明 --> https://hexo.io/docs/configuration.html](https://hexo.io/docs/configuration.html)
