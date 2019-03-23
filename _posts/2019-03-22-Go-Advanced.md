---
layout: post
title: "golang 进阶"
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

## 跳出 for-switch 和 fo-select 代码块

没有指定标签的 break 只会跳出 switch/select 语句，若不能使用 return 语句跳出，可以为 break 跳出标签指定的代码块。

*goto* 虽然也能跳转到指定位置，但是会再次进入 for-switch，形成死循环。

``` golang
func main() {
loop:
    for {
        switch {
        case true:
            fmt.Println("break")
            break
        }
    }
    fmt.Println("done")
}
```

## defer 函数的参数值

对 defer 延迟执行的函数，它的参数会在声明时候就执行表达式，而不是执行函数的时候才执行。

``` golang
func main() {
    var i = 1
    defer fmt.Println("result: ", func() int {return i * 2}())
    i++
}
# result: 2
```