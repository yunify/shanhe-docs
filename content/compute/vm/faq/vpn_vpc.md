---
title: "登录VPN，远程连接云主机"
date: 2021-07-07T00:38:25+09:00
description: Test description
weight: 50
draft: false
enableToc: false
---

### 1. 登录申请到的VPN
![](../_images/vpn.jpg)

### 2. VPC网络创建端口转发

#### 1）进入云主机列表，查看需远程登录的云主机内网IP
![](../_images/ilist.png)

#### 2) 进入VPC网络详情-管理配置-端口转发
![](../_images/vpc.png)

#### 3）添加端口转发（以SSH 22端口转发为例）
![](../_images/port.png)

#### 4）应用修改，等待更新完成
![](../_images/submit.png)

### 3. 放开安全组下行规则

#### 1）进入安全组
![](../_images/vpc_sg.png)

---

![](../_images/sg.png)

#### 2）放开端口的下行限制
![](../_images/port1.png)

#### 3）应用修改，等待更新完成
![](../_images/apply.png)

### 4. 测试映射出的端口

#### 1）找到VPC网络的内网IP
![](../_images/inip.png)

#### 2）试用内网ip+端口测试
![](../_images/test.png)
