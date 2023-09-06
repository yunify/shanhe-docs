---
title: "intel"
description: Test description
draft: false
enableToc: false
keyword: test
weight: 4
---

## Intel环境变量加载

本集群安装有 Intel 编译器 2015-2020 版本，以及 Intel oneAPI 编译器 2021-2022 版本

![png](/chaosuan/environment/_image/intel-mpi.png)

环境变量拆分为 intel 和 intelmpi 两个（其中intel包含了MKL环境），若无特殊，则需要同时加载两个，例如

```bash
module load intel/2022 intelmpi/2022
```

拆分的目的在于有的时候仅仅需要intelmpi
