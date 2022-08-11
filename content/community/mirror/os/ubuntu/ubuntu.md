---
title: "ubuntu"
date: "2022-08-02"
description: Test description
draft: false
enableToc: false
keyword: mirror,ubuntu
weight: 5
---
# Ubuntu使用帮助

```
Ubuntu的仓库地址为：https://mirrors.shanhe.com/ubuntu/
Ubuntu-CD的镜像地址为：https://mirrors.shanhe.com/ubuntu-cdimage/
Ubuntu-Cloud的镜像地址为：https://mirrors.shanhe.com/ubuntu-cloud-images/
Ubuntu-Ports的仓库地址为：https://mirrors.shanhe.com/ubuntu-ports/
Ubuntu-Releases的镜像地址为：https://mirrors.shanhe.com/ubuntu-releases/
ubuntu-cloud-archive的镜像地址为：https://mirrors.shanhe.com/ubuntu-cloud-archive/   
```

### 1、备份配置文件
执行如下命令：

```
sudo cp -a /etc/apt/sources.list /etc/apt/sources.list.bak
```

### 2、修改sources.list文件
将http://archive.ubuntu.com和http://security.ubuntu.com替换成https://mirrors.shanhe.com，可以参考如下命令：

```
sudo sed -i "s@http://.*archive.ubuntu.com@https://mirrors.shanhe.com@g" /etc/apt/sources.list
sudo sed -i "s@http://.*security.ubuntu.com@https://mirrors.shanhe.com@g" /etc/apt/sources.list
```

Ubuntu 14.04，最后的效果如下：

```
deb https://mirrors.shanhe.com/ubuntu/ trusty main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ trusty main restricted universe multiverse
deb https://mirrors.shanhe.com/ubuntu/ trusty-security main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ trusty-security main restricted universe multiverse

deb https://mirrors.shanhe.com/ubuntu/ trusty-updates main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ trusty-updates main restricted universe multiverse

deb https://mirrors.shanhe.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ trusty-backports main restricted universe multiverse

## Not recommended
# deb https://mirrors.shanhe.com/ubuntu/ trusty-proposed main restricted universe multiverse
# deb-src https://mirrors.shanhe.com/ubuntu/ trusty-proposed main restricted universe multiverse
```

Ubuntu 16.04，最后的效果如下：

```
deb https://mirrors.shanhe.com/ubuntu/ xenial main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ xenial main restricted universe multiverse
deb https://mirrors.shanhe.com/ubuntu/ xenial-security main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ xenial-security main restricted universe multiverse

deb https://mirrors.shanhe.com/ubuntu/ xenial-updates main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ xenial-updates main restricted universe multiverse

deb https://mirrors.shanhe.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ xenial-backports main restricted universe multiverse

## Not recommended
# deb http://mirrors.shanhe.com/ubuntu/ xenial-proposed main restricted universe multiverse
# deb-src http://mirrors.shanhe.com/ubuntu/ xenial-proposed main restricted universe multiverse
```

Ubuntu 18.04，最后的效果如下：

```
deb https://mirrors.shanhe.com/ubuntu/ bionic main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ bionic main restricted universe multiverse
deb https://mirrors.shanhe.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ bionic-security main restricted universe multiverse

deb https://mirrors.shanhe.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ bionic-updates main restricted universe multiverse

deb https://mirrors.shanhe.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ bionic-backports main restricted universe multiverse

## Not recommended
# deb http://mirrors.shanhe.com/ubuntu/ bionic-proposed main restricted universe multiverse
# deb-src http://mirrors.shanhe.com/ubuntu/ bionic-proposed main restricted universe multiverse
```

Ubuntu 20.04，最后的效果如下：

```
deb https://mirrors.shanhe.com/ubuntu/ focal main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ focal main restricted universe multiverse
deb https://mirrors.shanhe.com/ubuntu/ focal-security main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ focal-security main restricted universe multiverse

deb https://mirrors.shanhe.com/ubuntu/ focal-updates main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ focal-updates main restricted universe multiverse

deb https://mirrors.shanhe.com/ubuntu/ focal-backports main restricted universe multiverse
deb-src https://mirrors.shanhe.com/ubuntu/ focal-backports main restricted universe multiverse

## Not recommended
# deb http://mirrors.shanhe.com/ubuntu/ focal-proposed main restricted universe multiverse
# deb-src http://mirrors.shanhe.com/ubuntu/ focal-proposed main restricted universe multiverse
```

### 3、更新索引
执行如下命令：

```
apt-get update
```

