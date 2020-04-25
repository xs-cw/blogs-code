---
title: "Leetcode986"
date: 2020-03-08T14:45:17+08:00
tags: [leetcode]
categories: [leetcode]
draft: false
---

## 986. 区间列表的交集

给定两个由一些闭区间组成的列表，每个区间列表都是成对不相交的，并且已经排序。

返回这两个区间列表的交集。

（形式上，闭区间 [a, b]（其中 a <= b）表示实数 x 的集合，而 a <= x <= b。两个闭区间的交集是一组实数，要么为空集，要么为闭区间。例如，[1, 3] 和 [2, 4] 的交集为 [2, 3]。）

**示例：**

![img](/img/interval1.png)

> 输入：A = [[0,2],[5,10],[13,23],[24,25]], B = [[1,5],[8,12],[15,24],[25,26]]
> 输出：[[1,2],[5,5],[8,10],[15,23],[24,24],[25,25]]
> 注意：输入和所需的输出都是区间对象组成的列表，而不是数组或列表。



提示：

1. `0 <= A.length < 1000 `
2. `0 <= B.length < 1000`
3. `0 <= A[i].start, A[i].end, B[i].start, B[i].end < 10^9`

 

## 思路

遍历A,先判断两个区间是否有交集,如果有,则交集取`max(A[i][0],B[j][0])`,`min(A[i][1],B[j][1])`



## 代码

```go
func intervalIntersection(A [][]int, B [][]int) [][]int {
	res := make([][]int, 0)
	for i := range A {
		for ii := 0; ii < len(B); ii++ {
			if B[ii][0] > A[i][1] {
				ii = len(B)
				continue
			}
			if B[ii][1] < A[i][0] {
				continue
			}
			r := []int{0, 0}
			if A[i][0] <= B[ii][0] {
				r[0] = B[ii][0]
			} else {
				r[0] = A[i][0]
			}
			if A[i][1] <= B[ii][1] {
				r[1] = A[i][1]
			} else {
				r[1] = B[ii][1]
			}
			if r[0] <= r[1] {
				res = append(res, r)
			}
		}

	}
	return res
}
```

