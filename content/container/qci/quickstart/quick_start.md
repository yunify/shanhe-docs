---
title: "容器实例服务 ECI 的使用"
description: Test description
draft: false
enableToc: false
keyword: 
---

## 容器组的使用指南

### 1. 创建公网 IP

在弹性容器页面中选择关联服务中的公网 IP， 进入公网 IP 的服务页面。

![img](../Quick-start.assets/ksnip_20201122-154457.png)

点击**申请**，创建出指定规格的公网 IP。

![img](../Quick-start.assets/ksnip_20201122-154827.png)

### 2. 创建安全组

回到之前的容器实例服务页面中，在关联服务中选择防安全组，进入安全组管理页面。

![img](../Quick-start.assets/ksnip_20201122-155246.png)

![img](../Quick-start.assets/ksnip_20201122-155407.png)

点击创建，指定安全组名称并确认以后，跳转到安全组的详情页。这里可以根据业务需要添加相关规则并应用安全组。

![img](../Quick-start.assets/ksnip_20201122-155859.png)

### 3. 创建私有网络

再次回到容器实例服务页面中，点击关联服务中的私有网络，进入私有网络服务页面。

![img](../Quick-start.assets/ksnip_20201122-161214.png)

点击创建，进入私有网络创建页面。

创建一个受管私有网络。

![img](../Quick-start.assets/ksnip_20201122-161614.png)

### 4. 创建 VPC 网络

切回容器实例服务页面中，点击关联服务中的 VPC 网络， 进入VPC 网络服务页面。

![img](../Quick-start.assets/ksnip_20201122-152647.png)

点击创建 VPC 网络进入 VPC 网络创建页面。

![img](../Quick-start.assets/ksnip_20201122-153608.png)

选择之前创建的安全组并点击创建。

![img](../Quick-start.assets/ksnip_20201122-160638.png)

进入 VPC 网络详情页，进入图形化页面，绑定公网 IP，并加入上面创建的私有网络，点击应用修改。

![img](../Quick-start.assets/ksnip_20201122-162123.png)

### 5. 创建容器服务

在容器实例服务页面中，点击创建。

![img](../Quick-start.assets/ksnip_20201122-162547.png)

在容器实例服务创建页面中指定容器镜像。

![img](../Quick-start.assets/ksnip_20201122-163431.png)

点击下一步。

![img](../Quick-start.assets/ksnip_20201211-135657.png)

如果需要挂载外部硬盘，可以在卷挂载页面指定，这里直接点击下一步。

![img](../Quick-start.assets/ksnip_20201122-165257.png)

指定上面创建的私有网络。

![img](../Quick-start.assets/ksnip_20201122-165438.png)

指定容器组的基本信息并创建。

![img](../Quick-start.assets/ksnip_20201122-165612.png)

### 6. 查看创建后的容器实例的状态

![img](../Quick-start.assets/ksnip_20201122-210956.png)