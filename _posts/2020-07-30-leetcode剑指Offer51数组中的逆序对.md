---
layout:     post
title:      leetcode剑指Offer51数组中的逆序对
subtitle:   leetcode Coding Interviews 51
author:     BY
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - Blog
---


## 前言

持续更新了

## 正文

### 问题来源

本问题来自leetcode上的剑指offer51题。 

### 问题描述

在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数。  

#### 示例 1:
```
输入: [7,5,6,4]
输出: 5
```

#### 分析：  
```
func reversePairs(nums []int) int {
    return mergeSort(nums, 0, len(nums)-1)
}

func mergeSort(nums []int, start, end int) int {
    if start >= end {
        return 0
    }
    mid := start + (end - start)/2
    cnt := mergeSort(nums, start, mid) + mergeSort(nums, mid + 1, end)
    tmp := []int{}
    i, j := start, mid + 1
    for i <= mid && j <= end {
        if nums[i] <= nums[j] {
            tmp = append(tmp, nums[i])
            cnt += j - (mid + 1)
            i++
        } else {
            tmp = append(tmp, nums[j])
            j++
        }
    }
    for ; i <= mid; i++ {
        tmp = append(tmp, nums[i])
        cnt += end - (mid + 1) + 1
    }
    for ; j <= end; j++ {
        tmp = append(tmp, nums[j])
    }
    for i := start; i <= end; i++ {
        nums[i] = tmp[i - start]
    }
    return cnt
}
```

#### 总结：
勤思考。  

## 结语
不管怎么样好好加油。  
