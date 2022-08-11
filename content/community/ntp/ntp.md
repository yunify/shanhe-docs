---
title: "ntp服务配置帮助文档"
date: "2022-08-09"
description: Test description
draft: false
enableToc: false
keyword: ntp
weight: 1
---

## 在服务器（172.30.0.11）上安装ntp server
### 安装软件包
```
# yum install -y ntp ntpdate
```
### 编辑配置文件
编辑配置文件/etc/ntp.conf ，配置之前记得先备份文件。   
删除所有 server  XXX 的行
#### 添加

```
#这句是手动增加的，意思是指定的192.168.1.0--192.168.1.254的服务器都可以使用ntp服务器来同步时间。
restrict 172.30.0.0 mask 255.255.248.0 nomodify notrap
#这句也是手动添加的
server 10.251.100.1
#间服务器为客户端提供时间同步服务。
fudge 127.127.1.0 stratum 10
```
### 重启ntp服务
```
systemctl restart ntpd
```
### 检查时间服务器是否正确同步
```
# ntpq -p
     remote refid st t when poll reach delay offset jitter
==============================================================================
*85.199.214.100 .GPS. 1 u 43 64 377 223.219 -13.767 5.263
```
### 设置开机启动
```
systemctl enable ntpd
```

## 在其他服务器上安装client

```
yum install ntp ntpdate -y
sed -i '/^server/s/^/#/g' /etc/ntp.conf
echo "server 172.30.0.11" >> /etc/ntp.conf
ntpdate 172.30.0.11
systemctl restart ntpd
systemctl enable ntpd
ntpq -p
```