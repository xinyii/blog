---
title: Shadowsocks 全攻略
date: 2017-07-29 22:56:52
categories:
  - Tool
tags:
  - Shadowsocks
  - Linux
  - VPS
---


### 前言

攻略主要的内容为Shadowsocks的搭建，从VPS服务器的购买，到Shadowsocks的安装优化。仅作学习作用。

### 开始

#### 第一步，购买VPS服务器

经过多方的对比，在这里我推荐购买适合个人使用的性价比较高的bandwagon（搬瓦工）VPS。

<!-- more -->

方案名 | 内存 | 硬盘 | 流量 | 价格 | 链接
--- | --- | --- | --- | --- | --- 
KVM架构6机房 | 512MB | 10GB | 500GB/月 | $2.99月、$19.9年 | [点我](https://bwh1.net/cart.php?a=confproduct&i=1)
KVM架构单机房 | 512MB | 10GB | 1000GB/月 | $2.99月、$19.9年 | [点我](https://bwh1.net/cart.php?a=confproduct&i=0)

价格换算：包年$19.9 ≈ ￥134，折合每月￥11.2。 在这个价格上还可以使用优惠码在购买时打折。优惠码：

- BWH1ZBPVK（6%）
- BWH1XZOBK（5.5%）
- BWH1NJJHL（4.5%）
- BWH1GFWZP（3.5%）
- BWH1FOXXE（3%）

选择方案，进入购买页面购买，新用户需要注册，支付时可以使用支付宝。具体购买教程：[http://banwagong.cn](http://banwagong.cn/gonglue.html)

#### 第二步，安装Shadowsocks服务端

购买成功后进入 [MyServices Page](https://bandwagonhost.com/clientarea.php?action=products)
然后进入KVM控制面板 `KiwiVM Control Panel`
在这里可以修改操作系统，建议安装 `centos-7-x86_64-bbr`
然后修改ssh登录密码，设置成功后通过ssh登录服务器，开始安装Shadowsocks服务端


##### 安装

CentOS:
```
yum install python-setuptools && easy_install pip
pip install shadowsocks
```

Debian / Ubuntu:
```
apt-get install python-pip
pip install shadowsocks
```

##### 修改配置文件

创建或修改配置文件 `/etc/shadowsocks.json` 例如：
```json
{
    "server":"my_server_ip",
    "server_port":8388,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"mypassword",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false
}
```

配置说明

名称 | 说明
--- | ---
server | 服务监听IP地址，设置为本机外网ip
server_port | 服务监听端口，推荐设置为443
local_address | 本地监听ip地址
local_port | 本地监听端口
password | 密码
timeout | 超时，秒
method | 加密方式，默认 `aes-256-cfb`
fast_open | 是否启用 `TCP_FASTOPEN`
workers | 进程数，仅 Unix/Linux 有效

##### 启动与停止

```
ssserver -c /etc/shadowsocks.json -d start
ssserver -c /etc/shadowsocks.json -d stop
```

#### 第三步，使用Shadowsocks客户端

##### 客户端下载

- [Windows](https://github.com/shadowsocks/shadowsocks-windows/releases) / [OS X](https://github.com/shadowsocks/shadowsocks-iOS/releases)
- [Android](https://github.com/shadowsocks/shadowsocks-android/releases) / [iOS](https://github.com/shadowsocks/shadowsocks-iOS/wiki/Help)
- [OpenWRT](https://github.com/shadowsocks/openwrt-shadowsocks)

##### 客户端配置

Windows客户端为例，启动后右键系统任务栏图标 -> 服务器 -> 编辑服务器
填入Shadowsocks对应的服务配置，保存

##### 客户端使用

右键系统任务栏图标 -> 启动系统代理
登录 [google.com](https://www.google.com/) 测试

#### 第四步，优化Shadowsocks配置

[参考链接](https://github.com/iMeiji/shadowsocks_install/wiki/shadowsocks-optimize)

### 结语

翻墙不易，且行且珍惜。
（请勿用于商业或其他任何违法用途）