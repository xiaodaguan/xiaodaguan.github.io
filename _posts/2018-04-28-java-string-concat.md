---
layout: post
title: String 拼接那些事儿
date: 2018-04-28
categories: blog
tags: [java]
description: 
---



# String 拼接那些事儿

- StringBuffer 和StringBuilder
  - StringBuffer 的方法都是同步的
    - 为什么存在？可能是最早设计的时候没有考虑清楚
    - StringBuffer 基本上没有应用的场景
    - 因此在1.5的时候推出了非线程安全的StringBuilder。
    - 其实只要使用StringBuilder就好了，需要线程安全的string拼接场景基本不存在。
  - StringBuilder
    - 1.5同时所有'+'连接的String运算都隐式的使用StringBuilder。
    - 但是循环中对String直接使用'+'拼接会导致创建多个StringBuilder，降低性能。
  - String.concat
    - 每次调用返回一个new String()
- 性能比较
  - 循环拼接10000次
    - 结果：
      - concat: 152ms 150405336ns
      - '+': 812ms 811459215ns
      - builder: 1ms 694256ns
    - buidler 效率明显高，concat要比'+'效率高，猜测是因为concat每次创建string，而'+'每次创建StringBuilder(编译器对于循环的优化不智能)，创建StringBuiler 的开销要比String 大
  - 循环创建对象10000次
    - 结果：
      - string: 0ms 223664ns
      - builder: 2ms 1883333ns
    - 创建stringbuilder 的开销确实比string大很多
