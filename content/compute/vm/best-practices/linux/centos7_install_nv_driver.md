---
title: "CentOS 7 安装nvidia GPU驱动"
date: 2021-02-04T20:38:25+09:00
description: Test description
weight: 40
draft: false
enableToc: false
---

### 1. 查看云服务器上的GPU

    lspci

![](../../_images/lspci.jpg)

    安装lspci
    yum install pciutils -y

### 2. 安装内核源码，内核源码的版本须和服务器的内核版本一致

#### 1）查看内核版本

    uname -r

![](../../_images/uname.png)

#### 2）下载对应版本的内核源码包，需要系统内核版本完全一致

> 浏览器下载较慢，可使用迅雷等工具下载

    kernel-headers下载地址：https://pkgs.org/download/kernel-headers

![](../../_images/header.jpg)

![](../../_images/header2.png)

    kernel-devel下载地址：https://pkgs.org/download/kernel-devel

![](../../_images/devel.jpg)

![](../../_images/devel2.png)

#### 3）把kernel-devel 和 kernel-headers上传到服务器并安装

![](../../_images/install-kernel.png)

### 3. 禁用nouveau

> nouveau是一个第三方开元的Nvidia驱动，一般Linux系统安装的时候都会默认安装这个驱动。这个驱动会与nvidia官方
的驱动冲突，在安装nvidia驱动和cuda之前应该先禁用nouveau

#### 1) 查看系统是否正在使用nouveau

    lsmod | grep nouveau

![](../../_images/nouveau.png)

#### 2) 如果有任何输出，那么就是nouveau在启用，需要关闭，可按照以下步骤

    #打开如下文件
    vi /usr/lib/modprobe.d/dist-blacklist.conf

    #写入以下内容
    blacklist nouveau
    options nouveau modeset=0

    #保存并退出
    :wq

    #备份当前的镜像
    mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r).img.bak

    #建立新的镜像
    dracut /boot/initramfs-$(uname -r).img $(uname -r)

    #重启
    reboot

    #最后输入上面的命令验证
    lsmod | grep nouveau

    #直到没有任何输出，说明nouveau禁用了

### 4. 验证系统是否有GCC编译环境

    gcc -v

    -bash: gcc: command not found，则未安装，需要安装gcc

    yum install gcc -y

### 5. 安装驱动

#### 1）打开NVIDIA驱动下载链接
http://www.nvidia.com/Download/Find.aspx

#### 2）选择核实版本的驱动，包括产品系列、操作系统、语言、CUDA Tookit等

![](../../_images/driver.png)

    点击SEARCH

![](../../_images/search.png)

    点击下载，下载完成为.run后缀的文件

#### 3）执行.run脚本，安装驱动

![](../../_images/run.png)

![](../../_images/run2.png)

![](../../_images/run3.png)

![](../../_images/run4.png)

#### 4）验证驱动安装

    nvidia-smi

![](../../_images/smi.png)

