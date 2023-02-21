---
title: "数据类型"
weight: 1
bookFlatSection: false
bookCollapseSection: true
---

# Redis 的数据类型
Redis支持的数据类型概述

Redis 是一个数据结构服务器。Redis的核心是提供了一个本地数据类型集合，帮你解决各种各样的问题，从[缓存]()到[队列]()再到[事件处理]()。以下是每种数据类型的简要述，点击链接查看详细说明和参考命令。

如果你想尝试全面的教程，查看[Redis 数据类型指南]()。

## 核心

### Strings

[Redis strings]() 是最基础的 Redis 数据类型，表示一个字节的序列。更多详细信息，请看：

* [Redis strings 概述]()
* [Redis string 命令参考]()

### Lists

[Redis lists] 是一个按插入顺序排序的字符串列表。更多详细信息，请看：

* [Redis lists 概述]()
* [Redis list 命令参考]()

### Sets

[Redis sets]() 是不重复字符串的无序集合，就像您最喜欢的编程语言（例如 [Java HashSets](https://docs.oracle.com/javase/7/docs/api/java/util/HashSet.html)，[Python sets](https://docs.python.org/3.10/library/stdtypes.html#set-types-set-frozenset) 等）中的集合一样。你可以在 O(1) 时间复杂度的情况下增加、删除、校验 Redis set 中的元素是否存在（换句话说，这些操作与 set 中的元素个数无关）。更多详细信息，请看：

* [Redis sets 概述]()
* [Redis set 命令参考]()

### Hashes

[Redis hashes]() 是键值对集合的类型。因此，Redis hashes 与 [Python dictionaries](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)、[Java HashMaps](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html) 和 [Ruby hashes](https://ruby-doc.org/core-3.1.2/Hash.html) 类似。更多详细信息，请看：

* [Redis hashes 概述]()
* [Redis hashes 命令参考]()

### Sorted sets

[Redis sorted sets]() 是不重复字符串的集合，以每一个字符串的分数排序。更多详细信息，请看：

* [Redis sorted sets 概述]()
* [Redis sorted set 命令参考]()

### Streams

[Redis stream]() 是一种类似只能追加记录的日志的数据结构。Streams 按照事件的发生顺序进行记录并将它们联合处理。更多详细信息，请看：

* [Redis Streams 概述]()
* [Redis Streams 命令参考]()
* [Redis Streams 指南]()

### Geospatial indexes

[Redis geospatial indexes]() 对于查找给定地理半径或边界框内的位置非常有用。更多详细信息，请看：

* [Redis geospatial indexes 概述]()
* [Redis geospatial indexes 命令参考]()

### Bitmaps

[Redis bitmaps]() 使你在字符串上执行位运算。更多详细信息，请看：

* [Redis bitmaps indexes 概述]()
* [Redis bitmap indexes 命令参考]()

### Bitfields

[Bitfields]() 有效地编码字符串值中的多个计数器。Bitfields 提供原子的 get、set 和 increment 操作，并支持不同的溢出策略。更多详细信息，请看：

* [Redis bitfields 概述]()
* [Redis bitfield 命令参考]()

### HyperLogLog

[Redis HyperLogLog]() 数据结构提供了大集合基数（即元素数量）的概率估计。更多详细信息，请看：

* [Redis HyperLogLog 概述]()
* [Redis HyperLogLog 命令参考]()

### 扩展
要扩展内置的数据类型所提供的特性，请使用以下选项之一：
1. 编写自己的自定义的 [Lua 服务器端函数]()。
2. 使用 [modules API]() 编写自己的 Redis 模块，或者查看[社区支持的模块]()。
3. 使用 [Redis Stack]() 提供的 [JSON]()、[querying]()、[time series]()，和其他功能。