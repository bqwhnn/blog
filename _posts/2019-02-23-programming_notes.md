---
layout: post
title: "编程笔记"
description: "记录一些编程相关的东西"
categories: [note]
tags: [note]
redirect_from:
  -- /2019/02/23
---

* Kramdown table of contents
{:toc .toc}

# 服务器

## 分布式和集群

分布式：一个业务拆分成多个子业务，部署在不同的服务器上

集群：同一个业务，部署的多个服务器上

## 并发

在讨论并发的时候，如果说 a 早于 b 发生，那么我们就保证了 a 发生的时间一定早于 b，而且是可以预期的。

当 a 既不比 b 早也不比 b 晚，我们说 a 和 b 并发，这并不说明 a 和 b 一定同时发生，只说明我们不能确定它们的顺序。


[分布式和集群的区别](https://www.zhihu.com/question/20004877)