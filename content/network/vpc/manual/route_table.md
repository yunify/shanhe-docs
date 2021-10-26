---
title: "使用路由表"
linkTitle: "使用路由表"
description:
draft: false
weight: 40
---

[路由表 ( Routing Table )](https://zh.wikipedia.org/wiki/%E8%B7%AF%E7%94%B1%E8%A1%A8)可以为资源提供 IP 网络的[路由](https://www.ietf.org/rfc/rfc1812.txt)选择，通过配置**目标网络**及其**下一跳**，指定网络的路由方向，从而实现网络的连通和优化。

目前可以支持为私有网络 ( Vxnet ) 和负载均衡器 ( Load Balancer, LB ) 绑定路由表。

## 为私有网络添加路由规则

场景：私有网络云服务器统一通过 NAT 网关访问互联网，以实现公网 IP 地址的复用和带宽共享。

假设，用户的私有网络“办公网络”（ 192.168.128.0/24 ）内的所有虚拟机希望统一通过 NAT 网关 （ nat-00001 ）访问互联网。NAT 网关配置，请参见 [NAT 网关配置详情](/network/nat_gateway/manual/nat_user_guide/)。

### 创建路由表

在路由表页面，点击**创建**，**关联资源类型**选择**私有网络**。

<img src="../_images/create_route_table.png" style="zoom:50%;" />

路由表只需设置名称即可。

### 添加路由表规则

点击路由表 ID，进入路由表详情页面，点击**添加路由**。

目标网络：即私有网络要访问的目标网络，在本示例中为所有 IP 地址，即 0.0.0.0/0。

>**说明**
>
>  目的网络为 0.0.0.0/0 的路由规则也称**默认路由**。

下一跳类型：本示例中，网络的下一跳类型是 NAT 网关

下一跳：本示例中，网络的下一跳为 nat01 

<img src="../_images/add_routetable_default.png" style="zoom:50%;" />


然后执行应用修改


## 为负载均衡器添加路由规则

场景：云服务器通过隧道访问其他 VPC 的负载均衡器。

假设，用户数据中心的网络（ 192.168.10.0/24 ） 和 VPC 网络（ 172.16.10.0/24 ）通过隧道打通。

用户数据中心云服务器 192.168.10.2 (以下称“客户端”)，希望访问位于 VPC 中的"公私网混合 LB （ 172.16.10.253 ）"。

### 测试隧道连通情况

#### 客户端 ping 云服务器（假设 172.16.10.5 ）

登录 192.168.10.2 

```
    [root@route-table ~]# ip a 
    [root@route-table ~]# ping 172.16.10.5
```


![](../_images/ping_vpn_instance.jpg)

![](../_images/ping_vpn_instance2.jpg)

#### 添加 LB 监听器和后端

需要确保 LB 有后端服务器，才可以被访问。

#### 客户端 ping 公私网混合 LB 

```
    [root@route-table ~]# ping 172.16.10.253
```

![](../_images/ping_vpn_lb1.jpg)

### 配置路由表

#### 创建路由表

在路由表页面，点击**创建**，**关联资源类型**选择**负载均衡器**。

<img src="../_images/create_route_table_2.png" style="zoom:50%;" />

#### 添加路由表规则

点击路由表 ID，进入路由表详情页面，点击**添加路由**。

目标网络：希望资源能够访问的 IP 网络即 LB 要访问的目标网络，在本示例中为 192.168.10.0/24 。

下一跳：下一跳路由即 LB 所在网络。

<img src="../_images/add_route_table_rules.png" style="zoom:50%;" />

#### 绑定/解绑路由表

可以在路由表页面，右键单击路由表绑定/解绑 LB 。

<img src="../_images/router_bind_lb.png" style="zoom:50%;" />

也可以在 LB 页面，右键单击 LB 绑定/解绑路由表。

<img src="../_images/lb_bind_router.png" style="zoom:50%;" />

#### 客户端 ping 公私网混合 LB

```
    [root@route-table ~]# ping 172.16.10.253
```

![](../_images/ping_vpn_lb2.jpg)


## 路由表使用限制

资源只能绑定一个路由表，并且路由表关联类型需要与资源类型相同；

一个路由表可以绑定多个相同类型的资源 ；

暂不支持批量绑定和解绑。

