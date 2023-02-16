---
title: "关于"
weight: 1
bookFlatSection: false
---

# Redis 简介
了解 Redis 开源项目

Redis 是一个开源（BSD 许可）的内存数据结构存储系统，被用作数据库、缓存、消息中间件和流式引擎。Redis 提供了 [string]()、[hashes]()、[lists]()、[sets]()、[sorted sets]()、[bitmaps]()、[hyperloglogs]()、[hyperloglogs]()、[geospatial indexes]()和[streams]()等 [数据结构]()。Redis 内置[副本]()、[Lua 脚本]()、[LRU 淘汰机制]()、[事务]()和不同级别的[磁盘持久化]()，并通过[Redis 哨兵]()和[Redis 集群]()自动分区来保证其高可用。

你可以对这些类型执行原子性操作，如[string 追加字符串]()；[增加 hash 中的值]()；[往 list 中添加元素]()；[计算 set 的交集、并集和差集]();或者[在 sorted set 中获取最高分数的成员]()。

为了获取最佳性能，Redis 使用基于内存的数据集。根据你的使用情况，Redis 可以通过定期[转储数据集到磁盘]()或通过[追加每个的命令到基于磁盘的日志]()中来持久化你的数据。如果你只需要一个功能丰富的，使用内存的联网缓存，你也可以禁用持久化功能。

Redis 支持[异步副本]()，具有快速的非阻塞同步和在网络分裂时自动重连并进行部分同步的能力。

Redis还包括：
* [事务]()
* [发布/订阅]()
* [Lua 脚本]()
* [具有过期时间的主键]()
* [主键的 LRU 淘汰机制]()
* [自动故障转移]()

你能通过[大多数编程语言]()使用Redis。

Redis 使用 ANSI C 编写，适用于大多数 POSIX 系统，如 Linux、*BSD 和 Mac OS X，无需外部依赖。 Linux 和 OS X 是 Redis 开发和测试最多的两个操作系统，我们推荐使用 Linux 进行部署。 Redis 可以在 SmartOS 等 Solaris 派生系统中工作，并尽力支持。 Windows 版本没有官方支持。

[谁在使用 Redis？]()

选择在生产中运行 Redis 的组织列表

[Redis 开源管理]()

Redis 开源项目的管理模型

[Redis 发布周期]()

Redis 的新版本是如何发布的？

[Redis 发起人]()

现任和前任 Redis 发起人

[Redis 许可证]()

Redis 许可证和商标信息

[企业版]()

了解 Redis 企业版