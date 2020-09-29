---
layout:     post
title:      leetcode剑指Offer06从尾到头打印链表
subtitle:   leetcode Coding Interviews 06
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

本问题来自leetcode上的剑指offer06题。 

### 问题描述

输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。  

#### 示例 1:
```
输入：head = [1,3,2]
输出：[2,3,1]
```

#### 分析：  
```
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reversePrint(head *ListNode) []int {
    res := make([]int, 0)
    var dfs func(head *ListNode)
    dfs = func(head *ListNode) {
        if head == nil {
            return
        }
        dfs(head.Next)
        res = append(res, head.Val)
    }
    dfs(head)
    return res
}
```
看到有更短的做法  
```
func reversePrint(head *ListNode) []int {
        if head != nil {
        return append(reversePrint(head.Next), head.Val)
    }

    return nil
}
```

#### 总结：
勤思考。  

## 结语
不管怎么样好好加油。  
