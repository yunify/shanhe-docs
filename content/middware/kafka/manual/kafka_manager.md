---
title: "Kafka-manager 配置"
description: test
weight: 4
draft: false
---

## 自动添加集群配置到 Kafka-manager

Kafka 集群创建完后，客户端节点预装的 Kafka Manager 会自动加载 Kafka 集群的相关配置。


## 手动添加集群配置到 Kafka-manager  

### 详细步骤

配置[VPN](/network/vpc/manual/vpn/) 或[端口转发](/network/vpc/faq/methods_of_port_forwarding/)后，确保本地可以访问集群网络。如下图所示，在本地浏览器里输入```http://客户端节点IP:端口```，端口可以在集群配置参数进行设置0，默认为900。

> **说明**
>
>如果使用的版本是 Kafka 0.10.2.1 - ShanHe 1.1.6，可使用集群内任意节点的 IP。

![](../../_images/clusters.png)

1. 如果配置时指定需要登录，请使用配置的帐号登录。

2. 选择 **Cluster** -> **Add Cluster**。

3. 自定义一个名字，填写所连接的 Kafka 集群地址，山河提供的 Kafka 服务对应的命名空间路径为：zkhost1: port , zkhost2 : port… / kafka / 集群 ID。

   **例如**：Kafka集群id为 cl-j0yf8y1m, ZooKeeper地址 : 192.168.0.1:2181, 192.168.0.2:2181, 192.168.0.3:2181, 则填写192.168.0.1:2181, 192.168.0.2:2181, 192.168.0.3:2181/ kafka / cl-j0yf8y1m。

4. 选择 Kafka 对应的版本，例如 Kafka 版本为1.1.1，可以选择 1.1.1，勾选 jmx 配置。

5. 更改基本配置，点击 **save** 后可以使用 Kafka-manger 来管理和监控 Kafka 集群了。

![](../../_images/add_cluster.png)

## Kafka-manager升级说明

若集群由老版本升级时，会出现 Kafka-manager 的管理界面数据没有及时更新现象。这是由于 Kafka 实际版本已经更新，而 Zookeeper 中的注册数据未刷新，不影响正常使用。

操作步骤如下所示：

1. **Disable 集群**

   ![](../../_images/disable_cluster.png)

2. **Enable 集群**

   ![](../../_images/enable_cluster.png)

3. **恢复正常数据**

   ![](../../_images/recover_data.png)

### 最终效果图

![](../../_images/cluster_info.png)