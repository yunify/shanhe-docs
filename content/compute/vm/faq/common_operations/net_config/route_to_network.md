---
title: "自定义路由表配置网关服务器"
date: 2020-06-05T00:38:25+09:00
description: Test description
weight: 40
draft: false
enableToc: false
---

## 概述

在本项目中，您将了解如何使用云服务器自建一个网关服务器，让其他云服务器可以使用网关服务器访问互联网。

## 配置步骤

一、创建两台云服务器加入 VPC 的同一私有网络中

二、使用云服务器配置网关服务器，因此给这台云服务器绑定一个公网 IP

三、创建一个路由表，并在 VPC 的私有网络中绑定

四、配置路由规则

五、进入192.168.2.2 云服务器内部配置开启云服务器的路由功能

```
vim /etc/sysctl.conf

net.ipv4.ip_forward = 1
sysctl -p /etc/sysctl.conf
```

六、进入云服务器内部配置 iptables 策略

```
iptables -t nat -A POSTROUTING -s 192.168.2.0/24 -o eth0 -j SNAT --to-source 192.168.2.2
```

七、由于云服务器绑定了安全组，需要在安全组中放行 UDP 53端口放行 DNS ，否则解析不了域名

八、进入其它未绑定公网 IP 的云服务器 ping www.baidu.com 试验配置是否成功

![route_to_network06](../../../_images/route_to_network06.jpg)