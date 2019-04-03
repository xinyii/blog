---
title: Linux parted划分分区
categories:
- Linux
tags:
- Linux
---

#### parted命令简介

parted命令用来给2T以上的磁盘进行分区。而fdisk命令只能给2T以下的磁盘分区。

#### parted命令详解

parted命令分为两种模式：

- 命令行模式 `parted [option] device [command]` 
这种方式适用于编写脚本。

- 交互模式 `parted [option] device`


#### parted命令案例