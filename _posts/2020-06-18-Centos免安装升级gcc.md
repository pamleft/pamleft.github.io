---
layout:     post
title:      Centos免安装升级gcc
subtitle:   Centos Update Gcc not Compiled
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

今天编译代码的时候发现g++4.8.5不支持std的is_trivially_copy_constructible。这个是c++11标准中的。  

### 前言

CentOS 7虽然已经出了很多年了，但依然会有很多人选择安装CentOS 6，CentOS 6有些依赖包和软件都比较老旧，如今天的主角gcc编译器，CentOS 6的gcc版本为4.4，CentOS 7为4.8。gcc 4.8最主要的一个特性就是全面支持C++11，如果不清楚什么用的也没关系，简单说一些C++11标准的程序都需要gcc 4.8以上版本的gcc编译器编译，如MySQL 8.0版本(8.0.16以上版本是C++14标准，需gcc 5.3以上版本)。  
CentOS 6虽然是gcc 4.4的老旧版本，但是也可以升级gcc来安装gcc 4.8，我们今天就不采用编译安装的方法了，gcc安装起来非常费时，我们采用CentOS的一个第三方库SCL(软件选集)，SCL可以在不覆盖原系统软件包的情况下安装新的软件包与老软件包共存并且可以使用scl命令切换，不过也有个缺点就是只支持64位的。  
确定当前gcc版本，执行命令：gcc --version  
一般如果需要升级gcc至4.8或更高版本，建议直接采用安装SCL源之后安装devtoolset-6（devtoolset-6目前gcc版本为6.3），因为devtoolset-4及之前的版本都已经结束支持，只能通过其他方法安装  

#### 升级到gcc 7.3:
```
yum -y install centos-release-scl
yum -y install devtoolset-7-gcc devtoolset-7-gcc-c++ devtoolset-7-binutils
scl enable devtoolset-7 bash
```
需要注意的是scl命令启用只是临时的，退出shell或重启就会恢复原系统gcc版本。  
如果要长期使用gcc 7.3的话：  
```
echo "source /opt/rh/devtoolset-7/enable" >>/etc/profile
```
#### 升级到gcc 8.3：  
```
yum -y install centos-release-scl
yum -y install devtoolset-8-gcc devtoolset-8-gcc-c++ devtoolset-8-binutils
scl enable devtoolset-7 bash
```
需要注意的是scl命令启用只是临时的，退出shell或重启就会恢复原系统gcc版本。  
如果要长期使用gcc 8.3的话：  
```
echo "source /opt/rh/devtoolset-8/enable" >>/etc/profile
```
#### 升级到gcc 9.3：
```
yum -y install centos-release-scl
yum -y install devtoolset-9-gcc devtoolset-9-gcc-c++ devtoolset-9-binutils
scl enable devtoolset-9 bash
```
需要注意的是scl命令启用只是临时的，退出shell或重启就会恢复原系统gcc版本。  
如果要长期使用gcc 9.3的话：  
```
echo "source /opt/rh/devtoolset-9/enable" >>/etc/profile
```
#### 总结：
我这个只是做一个记录,原地址是在[为CentOS 6、7升级gcc至4.8、4.9、5.2、6.3、7.3等高版本](https://www.vpser.net/manage/centos-6-upgrade-gcc.html)  

## 结语
不管怎么样好好加油。  
