---
layout:     post
title:      leetcode剑指offer14-I剪绳子
subtitle:   leetcode Coding Interviews 14-I Cutting Rope
author:     BY
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - Blog
---


## 前言

又是好久没有更新了

## 正文

### 问题来源

本问题来自leetcode上的剑指offer14-I题。对应leetcode343题。  

### 问题描述

给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 k[0],k[1]...k[m-1] 。请问 k[0] * k[1] * ... * k[m-1] 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。   

#### 示例 1:
```
输入: 2
输出: 1
解释: 2 = 1 + 1, 1 × 1 = 1
```

#### 示例 2:
```
输入: 10
输出: 36
解释: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36
```

#### 分析：  
虽然好多年没学习高中数学知识，但是本能的反应就是每个相同相乘的数字与自然对数e相关。  
但是你让我证明，我也说不清所以然来。  
```
func cuttingRope(n int) int {
    if n == 2 {
        return 1
    }
    if n == 3 {
        return 2
    }
    if n % 3 == 1 {
        return int(math.Pow(3.0, float64(n/3-1)))*4
    }
    if n % 3 == 0 {
        return int(math.Pow(3.0, float64(n/3)))
    }
    return int(math.Pow(3.0, float64(n/3))) * 2
}
```
一行解决版本  
```
int cuttingRope(int n) {
    return n <= 3? n - 1 : pow(3, n / 3) * 4 / (4 - n % 3);
}
```

#### 总结：
勤思考。  

## 结语
不管怎么样好好加油。
