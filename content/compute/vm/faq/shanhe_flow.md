---
title: "山河资源使用指引"
date: 2021-07-07T00:38:25+09:00
description: Test description
weight: 50
draft: false
enableToc: false
---

### 1. 填写资源申请单

> 填写完成，发送邮件到 service@sdas.org

点击下载：

[国家超级计算济南中心用户试用使用申请表](https://jn1.is.shanhe.com/shanhe/web_file/%E5%9B%BD%E5%AE%B6%E8%B6%85%E7%BA%A7%E8%AE%A1%E7%AE%97%E6%B5%8E%E5%8D%97%E4%B8%AD%E5%BF%83%E7%94%A8%E6%88%B7%E8%AF%95%E7%94%A8%E4%BD%BF%E7%94%A8%E7%94%B3%E8%AF%B7%E8%A1%A8.doc)

### 2. 注册账号

https://console.shanhe.com/signup

![](../_images/register.png)

### 3. 身份认证

> 认证成功后会发放部分优惠券，供简单测试使用，如需提供更多优惠券支持，可联系超算对接人

两个认证入口：

#### 1）在激活邮件中，点击链接认证

![](../_images/id.png)

#### 2）登录系统后，进入 账户设置-认证信息 认证

![](../_images/id2.png)

### 4. 创建云服务器

#### 1）导航进入 计算-云服务器

![](../_images/instance.png)

#### 2）点击创建-选择系统

![](../_images/os.png)

#### 3）选择配置

![](../_images/config.png)

#### 4）选择网络

> 推荐使用VPC网络（专属私有网络）

![](../_images/vpcnet.png)

#### 5）基本信息

> 测试请使用按需计费

![](../_images/normal.png)

### 5. 申请VPN，远程连接云服务器

> 通过VPN： SSH、远程桌面、远程连接云服务器

> 填写VPN申请表，发送邮件到 service@sdas.org

点击下载：

[山河VPN申请表](https://jn1.is.shanhe.com/shanhe/web_file/%E5%B1%B1%E6%B2%B3%E5%85%AC%E6%9C%89%E4%BA%91VPN%E8%B5%84%E6%BA%90%E7%94%B3%E8%AF%B7%E8%A1%A8.docx)

> 注意：访问地址请填写VPC网络的内网地址

![](../_images/vpn_ip.png)

---

![](../_images/vpn_ip1.png)

> 通过VPN远程连接云主机，请参考：[登录VPN，远程连接云主机](https://docsv3.shanhe.com/compute/vm/faq/vpn_vpc/)

### 6. 云服务器访问互联网

#### 1）填写申请表，开通互联网的访问

> 发送申请外网的邮件到 service@sdas.org

    邮件内容：

    需访问互联网的VPC内网IP

    需要开通访问哪些外网地址或者全地址开通

> VPC内网IP，请按照下图方式查询

![](../_images/vpn_ip1.png)

