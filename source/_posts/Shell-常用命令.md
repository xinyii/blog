---
title: Shell 常用命令
date: 2016-10-27 14:20:36
categories:
  - Linux
tags:
  - Linux
  - Shell
---


#### 文本操作

- 打印
	- 全文 `cat <file>`
	- 首部 `head -<num> <file>`
	- 尾部 `tail -<num> <file>`
	- 跟踪 `tailf <file>`  

<!-- more -->

- 过滤
	- 匹配 `grep <regex> <file>`
	- 不匹配 `grep -v <regex> <file>`
	- 过滤注释与空行 `grep -v ^# <file>| grep -v ^$`
	- 去重 `sort <file> | uniq`
	- 重复行 `sort <file> | uniq -d`
	- 不重复行 `sort <file> | uniq -u`


- 统计
	- 统计行数 `wc -l`
	- 统计字数 `wc -m`


- 处理
	- 指定范围裁剪 `cut -c <N>-<M>`
	- 指定分隔符取词 `awk -F <separator> '{print $<num>}' <file>`

#### 文件操作

- 权限修改
	- 权限属性 `chmod <num> <file>`
	- 文件所属 `chown <user>:<group> <file>`
	- 文件加锁 `chattr +i <file>`
	- 文件解锁 `chattr -i <file>`


- 文件处理
	- 文件改名 `mv <file> <newfile>`
	- 文件复制 `cp <file> <newfile>`
	- 远程复制 `scp -P <port> <user>@<host>:<file> <newfile>`
	- 删除文件 `rm -rf <file>`


- 修改文件
	- 替换 `sed -i 's/<oldtext>/<newtext>/g' <file>`
	- 条件替换 `sed -i '/<regex>/s/<oldtext>/<newtext>/g' <file>`
	- 追加 `sed -i '$a <text>' <file>`


- 创建文件
	- 多级创建 `mkdir -p <file>`
	- 批量创建 `mkdir <prefix>{N..M}`


- 查找文件 `find . -name <file>`

#### 通用操作

- 程序执行
	- 程序后台运行 `nohup <command> &`
	- 程序并行执行 `<command> & <command>`
	- 程序顺序执行 `<command> && <command>` 或 `<command> ; <command>`
	- 程序切换后台执行 `ctrl + z` 然后`bg`
	- 程序切换前台执行 `fg`


- 输出重定向 `<command> &><file>`
- 管道 `<command> | <command>`
- 查看程序是否运行 `ps aux | grep <keyword>`
- 查看程序资源占用 `lsof -p <pid>`
- 查看后台执行程序 `jobs`


#### 远程操作

- 远程终端 `ssh -i <id_rsa> <host>`
- 远程执行命令 `ssh -i <id_rsa> <host> '<command>'`
- 测试连通 `ping <host>`
- 测试端口 `telnet <host> <port>`

#### 系统信息

- 系统版本
	- 发行版本 `cat /etc/issue`
	- 操作系统 `uname -a`
	- 内核信息 `cat /proc/version`


- 磁盘空间
	- 磁盘使用情况 `df -h`
	- 文件目录占用空间 `du -h`
	- 文件占用空间 `ls -lh`


- 网络
	- 查看网速 `iftop`
	- 查看端口 `netstat -apn | grep <port>`
	- 查看局网IP `ifconfig eth0 | grep "inet addr" | awk '{print $2}' | awk -F: '{print $2}'`
	- 查看外网IP `curl http://ip.cn 2>/dev/null | awk '{print $2}' | awk -F： '{print $2}'`


- 环境变量
	- 查看环境变量`set `
	- 设置环境变量 `export <key>=<value>`
	- 删除环境变量 `unset $<key>`
	- 设置永久环境变量 `echo "export <key>=<value>" >> /etc/profile`

#### 系统操作

- 注销 `exit`
- 关机 `shutdown -h now`
- 重启 `reboot`