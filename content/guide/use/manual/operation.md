---
title: "云资源标准化交付流程"
description: test
weight: 2
draft: false
---

本节提供山河公有云标准化资源交付流程，参考本节可在对云平台资源暂不了解的前提下完成标准化交付。
> 注：标准化交付以快速，安全，标准的原则进行，不涉及任何定制化操作。

## 需求示例

**前提要求：**

>已有山河云console（控制台）账户 <br>
>登录地址:[https://console.shanhe.com/login](https://console.shanhe.com/login) <br>
>已有山河云EasyConnect(VPN)账户 <br>
>登录地址:[https://124.128.58.194:4433](https://124.128.58.194:4433)

需求：创建一台云服务器，配置要求为 **4核CPU 4G内存，50G系统盘，100G数据盘，CentOS7.9系统**。<br>
要求虚机可以访问互联网，在用户本机可以ping通虚机，可以通过SSH登录虚机，虚机中有http服务，需要公网地址80端口上线,以提供对外访问。

## 查看配额

登陆控制台后，在[配额](/guide/use/intro/introduction/#2资源配额介绍)界面查看当前账户所拥有资源配额是否满足需求。

根据当前需求可判断需要配额为：
1. 网络： <br>
    VPC 网络 (个) >= 1 <br>
    私有网络 (个) >= 1 <br>
    公网IP (个) >= 1 <br>
    公网IP总带宽 (Mbps) >= 1
2. 计算： <br>
    基础型云服务器 (个) >= 1 <br>
    基础型CPU (核) >= 4 <br>
    基础型内存 (GB) >= 4 <br>
3. 存储： <br>
    容量型云盘(6) (块) >= 1 <br>
    容量型云盘(6)容量 (GB) >= 100 <br>
4. 安全： <br>
    安全组 (个) >= 1  <br>

如配额满足可进行下一步资源创建，如部分资源配额不如，可提[工单服务](/services/tickets/manual/operation/)申请资源配额。

## 资源创建

### 创建VPC

登录管理控制台后，在主页顶部的导航栏，点击**产品与服务**，然后在下拉菜单中，选择**VPC网络**，选择**创建VPC网络**。

弹出创建VPC网络界面后，**区域**选择山河云计算平台，**名称**自由设置，建议设置为项目名称，**IPv4地址范围**、**IPv6地址范围**、**类型**一般无需设置，默认即可。**公网IP**选择暂不绑定<br>**安全组**选择**新建安全组**，
![](../../_images/VPC2.png)

### 创建安全组

此时浏览器会自动新建标签页，打开安全组页面。在安全组页面点击蓝色**创建按钮**，输入安全组名称，建议使用项目名称，组内互信默认打开无需更改。
 <div style="text-align: center;">
  <img src="../../_images/anquanzu2.png" style="width: 80%; height: auto;">
  </div>

创建完安全组后进入所创建安全组规则界面，点击蓝色添加规则按钮，弹出添加规则界面：

![](../../_images/guiz.png)

根据需求描述，需要放通外部访问虚机的22端口、80端口以及ICMP报文，依次创建三条下行规则：<br>
对于常用端口云平台拥有快捷配置模版，点击右侧快捷方式下的ssh，填写自定义名称，点击提交。
>默认SSH协议使用22端口，http业务使用80端口，ping需要放行ICMP报文<br>
>外部访问虚机方向为下行

![](../../_images/guiz2.png)

再次蓝色添加规则按钮，点击右侧快捷方式下的http，填写自定义名称，点击提交。

![](../../_images/guiz3.png)

再次蓝色添加规则按钮，点击右侧快捷方式下的ping，填写自定义名称，点击提交。

![](../../_images/guiz4.png)

添加完安全组规则后，点击蓝色<font color="red"> 应用修改：</font>按钮，提示信息点击确认。

![](../../_images/guiz5.png)

等待右上角提示应用修改完毕后安全组创建完毕。

 <div style="text-align: center;">
  <img src="../../_images/guiz6.png" style="width: 50%; height: auto;">
  </div>

**浏览器返回新建VPC网络标签页**，点击安全组后的刷新按钮后，选择上述已新建安全组:

 <div style="text-align: center;">
  <img src="../../_images/VPC3.png" style="width: 100%; height: auto;">
  </div>

<br>

向下划动，在初始私有网络界面填写自定义名称，建议为项目名称，IPv4地址范围与网络ACL无需改动。

![](../../_images/VPC4.png)

点击立即创建，等待右上角提示VPC创建完成。

 <div style="text-align: center;">
  <img src="../../_images/VPC5.png" style="width: 50%; height: auto;">
  </div>

<font color="red"> 查看VPC内网IP地址，提交工单申请，申请所拥有VPN账号添加访问此内网IP权限，如需访问互联网，一并申请此内网IP访问互联网权限。</font>

![](../../_images/SSH.png)

### 创建云服务器

在主页顶部的导航栏，点击**产品与服务**，然后在下拉菜单中，选择**VPC网络**，点击上述新建VPC网络名称，进入具体VPC网络内部：

![](../../_images/VPC6.png)

默认展示新建私有网络项，在资源列表下点击**创建资源**，选择**云服务器**，进入创建云服务器界面：

![](../../_images/VPC7.png)

区域选择山河计算平台，依据需求选择规格为基础型4核4G，镜像选择CentOS7.9，系统盘为50G

![](../../_images/ECS2.png)

数据盘下选择新建数据盘，点击加号：

 <div style="text-align: center;">
  <img src="../../_images/ECS3.png" style="width: 50%; height: auto;">
  </div>

  弹出新建数据盘选项后，下拉选择容量型，大小选择100G。勾选自动格式化，数据盘将自动挂载到新建云服务器。

 <div style="text-align: center;">
  <img src="../../_images/ECS4.png" style="width: 70%; height: auto;">
  </div>

点击蓝色下一步按钮，进入网络配置界面，默认选择为上述新建VPC网络下私有网络，无需进行其他配置。

 <div style="text-align: center;">
  <img src="../../_images/ECS5.png" style="width: 180%; height: auto;">
  </div>

点击蓝色下一步按钮，进入系统配置界面，设置云服务器名称，选择登录方式为密码，设置云服务器密码（CentOS系统初始用户名为root）。

![](../../_images/ECS6.png)

右侧预览界面，选择计费方式，两种计费方式详见[计费模式](/compute/vm/billing/reserved_contract/)，选择完毕后，点击创建主机，等待右上角提示云服务器创建完成。

 <div style="text-align: center;">
  <img src="../../_images/ECS7.png" style="width: 50%; height: auto;">
  </div>

### SSH连接云服务器
创建完云服务器后，用户如需本地客户端登录（XShell、SecureCRT），需要用户使用VPC内网IP进行端口转发登录。

在主页顶部的导航栏，点击**产品与服务**，然后在下拉菜单中，选择**VPC网络**，点击上述新建VPC网络名称，进入VPC网络内部，找到内网IP地址：

![](../../_images/SSH.png)

<font color="red"> 确保已登录山河云EasyConnect(VPN)，且账户拥有此内网IP访问权限，如没有需提交工单申请权限。</font>

查看新建云服务器IP地址：

![](../../_images/SSH2.png)

点击管理配置，点击添加规则，添加端口转发：

![](../../_images/SSH3.png)

名称自定义；协议按需选择，SSH使用TCP；源端口为外部访问端口，当前只有一台虚机需要使用SSH，可直接填写22；内网IP为新建云服务器IP；内网端口为22。点击提交。

![](../../_images/SSH4.png)

提交完成后，在右上角点击蓝色<font color="red"> 应用修改：</font>按钮，等待更新完成。

 <div style="text-align: center;">
  <img src="../../_images/SSH5.png" style="width: 60%; height: auto;">
  </div>

在本地终端使用SSH连接VPC内网地址，端口为22，账号密码为新建云服务器账密，输入yes，云服务器密码，云服务器本地登录成功。

![](../../_images/SSH6.png)

### HTTP服务上线公网

云服务器本地开启http服务，以80端口为例，服务开启过程不再赘述：

![](../../_images/SSH7.png)

同样去VPC管理配置，添加口转发规则，<font color="red"> 应用修改：</font>

![](../../_images/HTTP.png)

此时在本地浏览器输入VPC内网IP地址加80端口，可以访问新建云服务器HTTP业务：

![](../../_images/HTTP2.png)

**此时业务必须用户登录特定权限VPN才能访问，如需业务能够从互联网直接访问，需要申请公网IP（EIP），并且通过上线检测：**

**1.申请公网地址：**

公网IP地址不能随意申请使用，在申请前需要在山河通提出申请，流程审批通过之后，会有工程师联系，协助开放公网IP配额和申请公网地址。

**2.业务端口上线检测：**

业务如有公网访问需求（拥有互联网访问入口），在上线前需要进行上线检测，有web界面的端口需要进行漏洞扫描和渗透测试，无web界面的端口只需要进行漏洞扫描。

提交工单申请，申请上线检测，提交工单时提供以下信息：
1.业务系统名称
2.业务地址URL（是否为web页面）
3.测试所用账号/密码
4.已申请公网地址及所使用端口

提交上线检测后，1-2天之内工程师回复检测报告，根据检测报告对所需修复漏洞进行修复，漏洞修复完成后联系工程师进行复测，复测通过后会直接开通公网地址业务端口。