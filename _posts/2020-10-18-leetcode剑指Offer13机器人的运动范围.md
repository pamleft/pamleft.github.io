---
layout:     post
title:      leetcode剑指Offer13机器人的运动范围
subtitle:   leetcode Coding Interviews 13
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

本问题来自leetcode上的剑指offer13题。 

### 问题描述

地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？  

#### 示例 1:
```
输入：m = 2, n = 3, k = 1
输出：3
```

#### 示例 2:
```
输入：m = 3, n = 1, k = 0
输出：1
```

#### 分析：  
```
func movingCount(m int, n int, k int) int {
    dp := make([][]bool, m)
    for i := 0; i < m; i++ {
        dp[i] = make([]bool, n)
    }
    dp[0][0] = true
    ans := 0
    for i := 0; i < m; i++ {
        for j := 0; j < n; j++ {
            if get(i) + get(j) > k {
                continue
            }
            if i > 0 {
                dp[i][j] = dp[i][j] || dp[i-1][j]
            }
            if j > 0 {
                dp[i][j] = dp[i][j] || dp[i][j-1]
            }
            if dp[i][j] {
                ans++
            }
        }
    }
    return ans
}

func get(x int) int {
    res := 0
    for x != 0 {
        res += x%10
        x /= 10
    }
    return res
}
```

#### 总结：
勤思考。  

## 结语
不管怎么样好好加油。  
