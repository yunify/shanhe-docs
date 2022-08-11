---
title: "Centos"
date: "2022-08-02"
description: Test description
draft: false
enableToc: false
keyword: mirror,centos
weight: 1
---

# Centos镜像源使用帮助

```
CentOS的镜像地址为：http://mirrors.shanhe.com/centos/
CentOS 6 及以下版本已被官网源下线, 若需使用, 请参考 CentOS-Vault 进行配置，CentOS-Vault的镜像地址为： http://mirrors.shanhe.com/centos-vault/
```

### 1、备份配置文件

```
cp -a /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak
```

### 2、两种方案，请大家自行选取。 

##### 方案一 下载新的CentOS-Base.repo文件到/etc/yum.repos.d/目录下，选择CentOS版本： CentOS 7 执行如下命令：

```
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.shanhe.com/help/conf/CentOS-7-reg.repo
```

CentOS 8 执行如下命令：

```
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.shanhe.com/help/conf/CentOS-8-reg.repo
```

##### 方案二 修改CentOS-Base.repo文件，取消baseurl开头的行的注释，并增加mirrorlist开头的行的注释。将文件中的http://mirror.centos.org替换成http://mirrors.shanhe.com，可以参考如下命令：

```
sed -i "s/#baseurl/baseurl/g" /etc/yum.repos.d/CentOS-Base.repo
sed -i "s/mirrorlist=http/#mirrorlist=http/g" /etc/yum.repos.d/CentOS-Base.repo
sed -i "s@http://mirror.centos.org@http://mirrors.shanhe.com@g" /etc/yum.repos.d/CentOS-Base.repo
```

### 3、清除原有yum缓存。 执行如下命令：

```
yum clean all
```

### 4、刷新缓存 执行如下命令：

```
yum makecache
```