---
title: "什么是消息队列 Kafka"
description: 
draft: false
enableToc: false
keyword: 
---

[Kafka](http://kafka.apache.org/) 是一种高吞吐量、低延迟、高可靠的分布式发布订阅消息系统。被广泛应用于网站活动追踪、日志监控、流式计算、事件采集、数据存储等应用场景。

山河提供的消息队列 Kafka 将 Kafka 通过云应用的形式在 AppCenter 部署，具有如下特性:

- 开箱即用，支持横向与纵向在线伸缩
- 系统自动健康检查，系统自动运维，降低企业使用成本
- 提供了监控告警功能更好的管理集群
- 节点上安装了Kafka-manager，可以管理和监控多个Kafka集群
- 提供文件查看器方便排查问题（版本 Kafka 1.1.1 - ShanHe 1.5.0 起）
- 提供第三方监控[zabbix](https://www.zabbix.com/)平台接口（版本 kafka 2.3.0 - ShanHe 2.0.0 起）

>**注意**
>
>Kafka 1.0.0 - ShanHe 1.1.6及后续新版本提供的Kafka-manager安装在客户端节点上。客户端节点用户名：ubuntu，密码：kafka。Kafka-manager 显示的版本并非实际Kafka版本，我们以创建 Kafka实 际版本为主，并不会影响到您使用 Kafka和 Kafka-manager。