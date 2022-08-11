---
title: "Epel"
date: "2022-08-02"
description: Test description
draft: false
enableToc: false
keyword: mirror,centos
weight: 2
---

# Epel 镜像源使用帮助

### 简介
```
EPEL (Extra Packages for Enterprise Linux), 是由 Fedora Special Interest Group 维护的 Enterprise Linux（RHEL、CentOS）中经常用到的包。

下载地址：https://mirrors.shanhe.com/epel/
```
### 备份配置文件
```
cp -a /etc/yum.repos.d/epel.repo  /etc/yum.repos.d/epel.repo.bak

```
### 安装epel-release
```
yum install epel-release -y
```
### 修改配置文件
修改/etc/yum.repos.d/epel.repo，将mirrorlist和metalink开头的行注释掉。  
接下来，取消注释这个文件里baseurl开头的行，并将其中的http://download.fedoraproject.org/pub替换成http://mirrors.shanhe.com。
```
sed -e 's!^metalink=!#metalink=!g' \
    -e 's!^#baseurl=!baseurl=!g' \
    -e 's!//download\.fedoraproject\.org/pub!//mirrors.shanhe.com!g' \
    -e 's!//download\.example/pub!//mirrors.shanhe.com!g' \
    -e 's!http://mirrors!https://mirrors!g' \
    -i /etc/yum.repos.d/epel*.repo
```
修改结果如下：（仅供参考，不同版本可能不同）
```
[epel]
name=Extra Packages for Enterprise Linux 7 - $basearch
baseurl=https://mirrors.shanhe.com/epel/7/$basearch
#metalink=https://mirrors.fedoraproject.org/metalink?repo=epel-7&arch=$basearch
failovermethod=priority
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7

[epel-debuginfo]
name=Extra Packages for Enterprise Linux 7 - $basearch - Debug
baseurl=https://mirrors.shanhe.com/epel/7/$basearch/debug
#metalink=https://mirrors.fedoraproject.org/metalink?repo=epel-debug-7&arch=$basearch
failovermethod=priority
enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
gpgcheck=1

[epel-source]
name=Extra Packages for Enterprise Linux 7 - $basearch - Source
baseurl=https://mirrors.shanhe.com/epel/7/SRPMS
#metalink=https://mirrors.fedoraproject.org/metalink?repo=epel-source-7&arch=$basearch
failovermethod=priority
enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
gpgcheck=1
```