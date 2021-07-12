---
title: "go泛型试用"
date: 2021-07-11T22:05:31+08:00
tags: [golang,go]
categories: [泛型]
draft: false
---

### go泛型试用

环境 Go1.17beta 

使用命令 `go build -gcflags=-G=3 `

```go
package main

import "fmt"

type name[T any] struct {
   data []T
}

func (x name[T]) mapFunc() name[T] {
   for i := range x.data {
      fmt.Println(x.data[i])
   }
   return x
}

func main() {
   vi := []int{1, 2, 3, 4, 5, 6}
   n := name[int]{data: vi}
   n.mapFunc().mapFunc()
}
```

> 也可以基于`dev.go2go`分支构建go，使用`go tool build xx.go2` 构建生成 .go文件
