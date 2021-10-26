---
title: "使用云服务器搭建一个基于LNMP的Wordpress博客"
description: test
draft: false
---

## 项目概览

在本项目中，您将了解如何使用山河 - 计算 - 云服务器部署具备高可用性的 LNMP Web 应用程序。本项目相关的技术栈有 Linux、Nginx、MySQL 和 PHP。

## 准备事项

山河账号：您需要注册一个山河账户并充值来购买资源。

操作系统：本地需使用Windows 7及以上版本的Windows操作系统。

技能水平：基本了解 Web 技术、命令行和 LNMP。

## 前期小知识

Wordpress是被广泛使用的、免费的、开放源代码的博客程序。相对于网易163博客或QQ空间等现成的博客网址，Wordpress具备更高的自定义特性：可以自定义网站的外观样式、可以自由地发表文章、可以绑定自己的域名、甚至可以在博客里面集成购物功能。国外的许多企业网址、摄影博客都是基于Wordpress构建的。

搭建一个Wordpress有非常多的方式，本文推荐的是通过LNMP一键包进行安装，帮助用户熟悉山河后台的基本操作以入门云计算。

LNMP就是Linux + Nginx + MySQL + PHP。针对非常小型的网址，可以不必完全使用LNMP方式来搭建，但LNMP可以良好应对未来流量上升而对服务器造成的压力，接触LNMP可以让我们在未来更好地深入学习。

* Linux：是一类Unix计算机操作系统的统称，是目前最流行的免费操作系统。代表版本有：debian、centos、ubuntu、fedora等。使用Linux而非Wordpress是因为Linux更省资源，Linux默认没有远程桌面也使得其比Windows更安全；
* Nginx：这是一个HTTP及反向代理引擎，其作用是作为一个中间人，让用户得以访问服务器上的资源。在用户量大后，也可作控制流量用，将用户分散到不同的服务器以减缓单个服务器的压力；
* MySQL：数据库软件，博客文章数据以及用户数据等都存储在MySQL的数据表里。数据库可以使数据的存储更有条理，也有方便快捷的语法可以批量调整数据；
* PHP：PHP是一个编程语言，Wordpress便是基于PHP编写，在服务器上配置好PHP才能使Wordpress正常运行。

## 具体操作

### 1. 创建云服务器

云服务器是通过虚拟化隔离出来具备特定算力的资源。以往机房会将CPU，硬盘，内存以固定的配比装配在一台服务器内。现在公有云机房会将CPU、硬盘、内存分散放在不同机柜，然后通过虚拟化技术对其进行调度，以有效地降低成本。云服务器则可以让用户不必顾虑底层的调度技术，而可以直接使用算力资源。

详情请参考[创建云服务器](/compute/vm/quickstart/create_vm)。

### 2. 远程连接服务器

接下来需要准备一个xshell软件进行服务器的远程控制。xshell提供免费的家庭版，可以在[这里下载](https://www.netsarang.com/zh/free-for-home-school/)。

安装完成后，按照下图操作。云服务器位置需填入刚刚申请的IPv4。

![1567415648489](../../_images/Build-Wordpress.assets/1567415648489.png)

![1567415742667](../../_images/Build-Wordpress.assets/1567415742667.png)

然后点击 用户身份验证 - 用户名填写ubuntu，密码填写创建云服务器时设定的SSH密码。

![1567415796913](../../_images/Build-Wordpress.assets/1567415796913.png)

![1567415899410](../../_images/Build-Wordpress.assets/1567415899410.png)

![1567415938811](../../_images/Build-Wordpress.assets/1567415938811.png)

### 3. 安装LNMP一键包

进入命令行后，输入`sudo su`以获取root权限，之后再一次输入创建云服务器时设定的SSH密码（输入的密码不会在命令行显示，输入完成后直接回车即可）。

![1567416142518](../../_images/Build-Wordpress.assets/1567416142518.png)

再敲入：`screen -S lnmp`

输入：`wget http://soft.vpser.net/lnmp/lnmp1.6.tar.gz -cO lnmp1.6.tar.gz && tar zxf lnmp1.6.tar.gz && cd lnmp1.6 && ./install.sh lnmp`

PHP版本等都保持默认即可。遇到下图所示情况，需要输入MySQL密码，请勿和SSH密码保持一致，本文为了演示方便使用了弱密码，请在实际操作时使用高强度的密码。

![1567416220495](../../_images/Build-Wordpress.assets/1567416220495.png)

接下来一路回车即可。

LNMP的安装时长视服务器的配置以及网络状态而定，安装完成时长普遍在20-40分钟。

![1567419397487](../../_images/Build-Wordpress.assets/1567419397487.png)

安装完成后打开浏览器，地址栏填入自己的IP即可查看是否安装成功。

![1567565153074](../../_images/Build-Wordpress.assets/1567565153074.png)

### 4. 安装Wordpress

在浏览器输入`(您的ip)/phpmyadmin`，如`123.123.123.123/phpmyadmin`，进入后新建一个名为`wordpress`的数据库。

![1567738905047](../../_images/Build-Wordpress.assets/1567738905047.png)

然后在Xshell终端依次输入：

`cd /home/wwwroot/default/`

`wget https://wordpress.org/latest.tar.gz`

`tar -zxvf latest.tar.gz`

在浏览器输入`(您的ip)/wordpress`，如`123.123.123.123/wordpress`，就可以到达如下界面：

![1567738656341](../../_images/Build-Wordpress.assets/1567738656341.png)

单击’Let’s go!‘按钮，在下图中，需要输入数据库信息，‘Database Name’就是刚刚创建的‘wordpress’，‘Usernmae’输入root，‘Password’输入在安装lnmp时设置的数据库密码。

![1567738735195](../../_images/Build-Wordpress.assets/1567738735195.png)

![1567739587642](../../_images/Build-Wordpress.assets/1567739587642.png)

如果在`Submit`后出现如下图所示问题：

![1567739601085](../../_images/Build-Wordpress.assets/1567739601085.png)

此时需要在Xshell终端输入`vi wp-config.php`创建一个`wp-config.php`文件，点击键盘`i`进入编辑模式，并将图中文本框内容复制进去，然后点击键盘`esc`并输入`:wq`保存退出，然后回到浏览器点击`Run the installation`继续。

安装完成后需要配置站点，在这里您需要设置的用户名和密码是网站的用户名和密码，是区别于云服务器，数据库的另一套系统，作用是访问网站管理后台。

![1567739619826](../../_images/Build-Wordpress.assets/1567739619826.png)

![1567739635983](../../_images/Build-Wordpress.assets/1567739635983.png)

安装完成后，再次访问`(您的ip)/wordpress`，如`123.123.123.123/wordpress`，就可以成功登陆到wordpress了~

![1567739761788](../../_images/Build-Wordpress.assets/1567739761788.png)

## 后期备案

若您希望正常运行自己的Wordpress博客，您便需要购买域名并解析到山河的ip。

根据中国大陆工信部的规定，所有在大陆境内运行的服务都必须进行 ICP 备案。只要在互联网能访问并且使用大陆公网 IP 地址的域名都需要备案。

备案完成后，将您的域名在域名提供商那里解析到山河的ip即可。