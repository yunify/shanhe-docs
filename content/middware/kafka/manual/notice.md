---
title: "注意事项"
description: test
weight: 16
draft: false
---

- 消息队列 Kafka 在 ZooKeeper 上注册路径格式如下：zk1:2181,zk2:2181,zk3:2181/kafka/cluster_id , cluster_id 是创建 Kafka 集群时候生成的集群 ID。
- 请尽量合理选择和预留存储资源，合理配置数据存储周期和大小，尽量避免因为磁盘写满而造成的线上故障。
- 开发的时候客户端尽量选择与服务端对应的版本。
- 可以使用 Kafka-manager 管理和修改 Topic 配置、监控集群，也可以使用客户端节点或者自己安装客户端，使用命令行形式管理和使用集群。
- offsets.topic.replication.factor参数必须小于或者等于 Kafka broker 节点数，不能大于 Kafka broker 节点数，否则就会消费不了消息，直至集群中 Kafka broker 节点数大于或者等于此参数。
- 您可以使用计算平台的[云监控CloudSat](/monitor_service/cloudsat/)与[自动伸缩](/operation/autoscaling/)功能为集群节点提供更强大的保障。

在使用过程中如果遇到问题可以通过[提交工单](https://console.shanhe.com/tickets/)来获取帮助，我们将竭诚为您服务。

