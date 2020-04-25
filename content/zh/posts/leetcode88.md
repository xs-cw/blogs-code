---
title: "Leetcode88"
date: 2020-03-07T21:30:36+08:00
tags: [leetcode]
categories: [leetcode]
draft: false
---
## 88. 合并两个有序数组
给你两个有序整数数组 `nums1` 和 `nums2`，请你将 `nums2` 合并到 `nums1` 中，使 `num1` 成为一个有序数组。

### 说明:

- 初始化 `nums1` 和 `nums2` 的元素数量分别为 m 和 n 。
- 你可以假设 `nums1` 有足够的空间（空间大小大于或等于 m + n）来保存 `nums2` 中的元素。
## 示例:

```go
输入:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

输出: [1,2,2,3,5,6]
```
## 思路

从`nums1`的最后一个位置(`i=len(nums1)-1`)开始依次填入两个数组中最大的;

因为两个数组都是有序的,所以只需要从最后的位置比较即可;

`nums1`与`nums2`比较下标为`m-1`和`n-1`,将两者中较大的移到`nums1`的尾部;

将取出数字的数组下标(m或者n)和`i`都往前移动一步,直到`nums2`取完.

若`nums1`的m<0,则只需要将`nums2`的剩余数字依次填充到`i`下标即可

## 代码

```go
func merge(nums1 []int, m int, nums2 []int, n int) {
	if m == 0 {
		copy(nums1, nums2)
		return
	}
	m--
	n--
	for i := len(nums1) - 1; i >= 0 && n >= 0; i-- {
		if m < 0 || nums1[m] <= nums2[n] {
			nums1[i] = nums2[n]
			n--
            continue
		}
		if nums1[m] > nums2[n] {
			nums1[i], nums1[m] = nums1[m], nums2[n]
			m--
		}
	}
}
```