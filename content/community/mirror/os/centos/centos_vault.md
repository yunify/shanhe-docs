---
title: "Centos vault"
date: "2022-08-02"
description: Test description
draft: false
enableToc: false
keyword: mirror,centos
weight: 3
---

# centos-vault镜像

## 简介

其中CentOS-Vault.repo对应的是发行该镜像时的yum源版本，使用该镜像源可以下载发行镜像时的yum源。

下载地址：https://mirrors.shanhe.com/centos-vault/

## 相关链接

官方主页：https://vault.centos.org/


### 配置方法
建议先备份 /etc/yum.repos.d/ 内的文件。

需要确定您所需要的小版本，如无特殊需要则使用该大版本的最后一个小版本，比如 6.10，5.11，我们将其标记为 $minorver，需要您在之后的命令中替换。

然后编辑 /etc/yum.repos.d/ 中的相应文件，在 mirrorlist= 开头行前面加 # 注释掉；并将 baseurl= 开头行取消注释（如果被注释的话）。 对于 CentOS 8 之前的版本，请把该行内的域名及路径（例如mirror.centos.org/centos/$releasever）替换为 mirrors.shanhe.com/centos-vault/$minorver。 对于 CentOS 8 ，请注意域名及路径发生了更换，此时需要替换的字段为 http://mirror.shanhe.org/$contentdir/$releasever

```
cp -a /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak
```

##### 修改CentOS-Vault.repo文件，取消baseurl开头的行的注释，并增加mirrorlist开头的行的注释。将文件中的http://mirror.centos.org替换成http://mirrors.shanhe.com，可以参考如下命令：

```
#  Centos 6
minorver=6.10
sudo sed -e "s|^mirrorlist=|#mirrorlist=|g" \
         -e "s|^#baseurl=http://mirror.centos.org/centos/\$releasever|baseurl=https://mirrors.shanhe.com/centos-vault/$minorver|g" \
         -i.bak \
         /etc/yum.repos.d/CentOS-*.repo

# CentOS 8 
minorver=8.5.2111
sudo sed -e "s|^mirrorlist=|#mirrorlist=|g" \
         -e "s|^#baseurl=http://mirror.centos.org/\$contentdir/\$releasever|baseurl=https://mirrors.shanhe.com/centos-vault/$minorver|g" \
         -i.bak \
         /etc/yum.repos.d/CentOS-*.repo

```
> 注意其中的 * 通配符，如果只需要替换一些文件中的源，请自行增删。
注意，如果需要启用其中一些 repo，需要将其中的 enabled=0 改为 enabled=1。

刷新缓存 执行如下命令：

```
yum makecache
```