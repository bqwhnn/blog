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

## 类型声明与方法

从一个现有的非 interface 类型创建新类型，不会继承原有的方法；  
将原类型以匿名字段的形式嵌到自定义的新的 struct 中，可以使用原类型的方法；  
使用 interface 类型创建新类型，保留了原类型的方法集。

``` golang
type Locker1 sync.Mutex

type Locker2 struct {
    sync.Mutex
}

type Locker3 sync.Locker

func main() {
    var locker Locker1
    locker.Lock() // 报错
    locker.Unlock() // 报错

    var locker Locker2
    locker.Lock() // OK
    locker.Unlock() // OK

    var locker Locker3
    locker.Lock() // OK
    locker.Unlock() // OK
}
```

## 堆栈变量

Go 编译器会根据变量的大小和 "escape analysis" 的结果来决定变量的存储位置，所以可以准确返回本地变量的地址。

在 go build 或 go run 时，加入 -m，能准确分析程序的变量分配的栈堆位置：

> go run -gcflags -m main.go

# 并发和锁

## nil channel

题目描述: 编写一个程序，开启 3 个线程 A,B,C，这三个线程的输出分别为 A、B、C，每个线程将自己的 输出在屏幕上打印 10 遍，要求输出的结果必须按顺序显示。如：ABCABCABC....

``` golang
package main

import (
    "fmt"
    "time"
)

func repeatin(ch chan string, s string) {
    for i := 1; i <= 30; i++ {
        ch <- s
    }
}

func main() {
    ch1 := make(chan string)
    ch2 := make(chan string)
    ch3 := make(chan string)

    go func() {
        var c1 <-chan string = ch1
        var c2 <-chan string
        var c3 <-chan string

        for {
            select {
            case val := <-c1:
                fmt.Print(val)
                c1 = nil
                c2 = ch2
            case val := <-c2:
                fmt.Print(val)
                c2 = nil
                c3 = ch3
            case val := <-c3:
                fmt.Print(val)
                c3 = nil
                c1 = ch1
            }
        }
    }()

    go repeatin(ch1, "A")
    go repeatin(ch2, "B")
    go repeatin(ch3, "C")

    time.Sleep(1 * time.Second)
}
```

在一个值为 nil 的 channel 上发送和接收数据将永久阻塞，利用这个死锁的特性，可以用在 select 中动态地选择发送或接收的 channel。

# 网站

[Go 手册](https://golang.google.cn/)

[Go 手册(中文)](https://go-zh.org/)

[Go 语言中文社区](https://github.com/Go-zh)

[Go 指南](https://tour.go-zh.org/list)

[实效 Go 编程](https://go-zh.org/doc/effective_go.html)

[Go walker](https://gowalker.org/)

[Go 夜读](https://github.com/developer-learning/reading-go)

[Go's Declaration Syntax, 为什么类型在变量后面](https://blog.go-zh.org/gos-declaration-syntax)

[Defer, Panic, and Recover](https://blog.go-zh.org/defer-panic-and-recover)

[Go 切片：用法和本质](https://blog.go-zh.org/go-slices-usage-and-internals#)

[Go 优缺点](https://bluxte.net/musings/2018/04/10/go-good-bad-ugly/)

[Go 文章](https://www.cnblogs.com/qcrao-2018/tag/Golang/)

[Go coding in go way](https://tonybai.com/2017/04/20/go-coding-in-go-way/)

[Go: the Good, the Bad and the Ugly](https://studygolang.com/articles/12907)