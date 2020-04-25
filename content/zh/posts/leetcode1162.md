---
title: "Leetcode1162"
date: 2020-04-04T00:43:32+08:00
tags: [leetcode]
categories: [leetcode]
draft: false
---
### 1162. 地图分析

你现在手里有一份大小为 N x N 的「地图」（网格） grid，上面的每个「区域」（单元格）都用 0 和 1 标记好了。其中 0 代表海洋，1 代表陆地，请你找出一个海洋区域，这个海洋区域到离它最近的陆地区域的距离是最大的。

我们这里说的距离是「曼哈顿距离」（ Manhattan Distance）：(x0, y0) 和 (x1, y1) 这两个区域之间的距离是 |x0 - x1| + |y0 - y1| 。

如果我们的地图上只有陆地或者海洋，请返回 -1。

示例1:

 ![img](/img/1336_ex1.jpeg)
```
输入：[[1,0,1],[0,0,0],[1,0,1]]
输出：2
解释： 
海洋区域 (1, 1) 和所有陆地区域之间的距离都达到最大，最大距离为 2。
```

**示例 2：**

 ![img](/img/1336_ex1.jpeg)

```
输入：[[1,0,0],[0,0,0],[0,0,0]]
输出：4
解释： 
海洋区域 (2, 2) 和所有陆地区域之间的距离都达到最大，最大距离为 4。
```

**提示：**

1. `1 <= grid.length == grid[0].length <= 100`
2. `grid[i][j]` 不是 `0` 就是 `1`

### 思路

筛选到所有陆地,逐个向外(四个方向)遍历一次,并将遍历到的海洋标记为已经遍历,记录下遍历距离,最后遍历到的海洋即是最远位置的,返回此时距离.

### 代码

```go
func maxDistance(grid [][]int) int {
	land := make([][]int, 0)
	length := len(grid)
    // 拓展方向
	dx := []int{1, -1, 0, 0}
	dy := []int{0, 0, 1, -1}
    // 记录陆地坐标
	for i := range grid {
		for i2 := range grid[i] {
			if grid[i][i2] == 1 {
				land = append(land, []int{i, i2})
			}
		}
	}
    // 没有陆地或者没有海洋返回-1
	if len(land) == 0 || len(land) == length*length {
		return -1
	}
	i := 0
	for ; i < len(land); i++ {
		x, y := land[i][0], land[i][1]
		for j := 0; j < 4; j++ {
			newX, newY := x+dx[j], y+dy[j]
			if newX < 0 || newY < 0 || newX >= length || newY >= length || grid[newX][newY] != 0 {
				continue
			}
			grid[newX][newY] = grid[x][y] + 1
			land = append(land, []int{newX, newY})
		}
	}
	i--
	x, y := land[i][0], land[i][1]
	return grid[x][y] - 1
}
```

