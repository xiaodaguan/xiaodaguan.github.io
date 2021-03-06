---
layout: post
title: Java学习之路(持续更新)
date: 2017-07-26
categories: blog
tags: [java, java基础, java高级特性]
description: 
---



## Java学习之路(持续更新)

一些感觉上比较核心的知识点，希望能不断学习

### JVM


>JVM的编译优化


#### GC
>JVM内存分代

>Java 8的内存分代改进


>GC是在什么时候，对什么东西，做了什么事情？

- 什么时候

能说出新生代、老年代结构，能提出minor gc/full gc
能说明minorgc/full gc的触发条件、OOM的触发条件，降低GC的调优的策略。
列举一些我期望的回答：
eden满了minor gc，升到老年代的对象大于老年代剩余空间full gc，或者小于时被HandlePromotionFailure参数强制full gc；
gc与非gc时间耗时超过了GCTimeRatio的限制引发OOM，调优诸如通过NewRatio控制新生代老年代比例，通过 MaxTenuringThreshold控制进入老年前生存次数等……
能回答道这个阶段就会给我带来比较高的期望了，当然面试的时候正常人都不会记得每个参数的拼写，我自己写这段话的时候也是翻过手册的。回答道这部分的小于2%。

- 对什么东西

从gcroot开始搜索，搜索不到的对象。
从root搜索不到，而且经过第一次标记、清理后，仍然没有复活的对象。

- 做什么事情

删除不使用的对象，腾出内存空间。
补充一些诸如停止其他线程执行、运行finalize等的说明。
能说出诸如新生代做的是复制清理、from survivor、to survivor是干啥用的、老年代做的是标记清理、标记清理后碎片要不要整理、复制清理和标记清理有有什么优劣势等。
除以上，还能讲清楚串行、并行（整理/不整理碎片）、CMS等搜集器可作用的年代、特点、优劣势，并且能说明控制/调整收集器选择的方式。

>GC策略都有哪些分类？

>这些策略分别都有什么优劣势？都适用于什么场景？


>实际的场景，选择一个GC策略，为什么？


#### 类加载


>类加载器都有哪些？都加载哪些类？
>这些类加载之间的父子关系是怎样的？
>什么是双亲委派模型？
>为什么要使用双亲委派模型？
>如何自定义自己的类加载器，自己的类加载器和Java自带的类加载器关系如何处理？


#### 内存

>内存分为哪几部分，这些部分分别都存储哪些数据？
>一个对象从创建到销毁都是怎么在这些部分里存活和转移的？
>内存的哪些部分会参与GC的回收？
>Java的内存模型是怎么设计的？为什么？
>结合内存模型的设计谈谈xxx?
>对Java内存模型的理解，以及其在并发中的应用

>指令重排序，内存栅栏等




### java语言·高级特性


#### 集合类：LinkedList, ArrayList, HashMap, TreeMap, LinkedHashMap
>TreeMap和LinkedHashMap是如何保证它的顺序的？哪个的有序实现比较好？


#### 并发包java.concurrent

>HashMap的并发问题

>如果想实现所有的线程一起等待某个事件的发生，当某个事件发生时，所有线程一起开始往下执行的话，有什么好的办法吗？

栅栏（Java的并发包中的CyclicBarrier）
>实现原理？其它的实现方式？哪个方式更好？

#### IO/NIO(NIO重点)
>selector, 职责和原理

核心：IO线程池

>IO包设计模式

装饰器模式
>为什么要这么设计？




### 设计模式

>在工作中遇到过哪些设计模式，是如何应用的

### 分布式

### 网络