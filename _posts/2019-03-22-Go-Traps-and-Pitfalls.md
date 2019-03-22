---
layout: post
title: "golang 陷阱与缺陷"
description:
categories: [go]
tags: [go]
redirect_from:
  -- /2019/03/22
---

* Kramdown table of contents
{:toc .toc}

# 陷阱

## 引用和指针

silce, map, channel 是引用，内部数据结构包含了底层数据结构的指针，所以作为函数参数在函数中改变其中的值能够生效。

其余数据类型在作为函数参数时，由于函数传参是值拷贝，所以如果需要在函数中改变值，就需要传指针。