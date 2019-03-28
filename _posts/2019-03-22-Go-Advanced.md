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

# 文章

[Go coding in go way](https://tonybai.com/2017/04/20/go-coding-in-go-way/)