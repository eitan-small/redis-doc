---
title: "Redis data types tutorial"
linkTitle: "Tutorial"
weight: 1
---

# Redis 数据类型指南
学习 Redis 基础数据类型及如何使用它们

以下是一个实操指南，教你使用 Redis 命令行操作 Redis 核心数据类型。有关数据类型的笼统概述，请参阅[关于](/docs/data-types)。

## Key

Redis Keys 是二进制安全的，这意味着你能使用任意二进制序列作为 key，包括 "foo" 这样的字符串或一个JPEG文件的内容。空字符串也是一个有效的 key。

关于 keys 的一些其他规则：
* 使用过长的 keys 不是一个好的主意。例如，一个 1024 个字节的 key，不仅在内存角度上不明智，而且在数据集上查找这些 key 需要耗费多次代价昂贵的 key 比较。即使当你手上的任务是匹配一个大值的存在，对其进行 hash （例如使用 SHA1） 是一个更好的选择，尤其是从内存和带宽的角度来看。
* 过短的 key 通常也不是一个好主意。如果你可以写 "user:1000:follower"，那么写 "u1000flw" 作为 key 就没什么意义了。前者可读性更强，而且 key 所增加的空间与对象本身的 value 所占空间相比是微不足道的，你的任务是在二者之间寻找一个合适的平衡。
*  试着使用一个模式。"object-type:id" 就是一个好主意，比如 "user:1000"。点或破折号通常用于多词字段，如 "comment:4321:reply.to" 或者 "comment:4321:reply-to"。
* key 最大允许 512 MB。

## String

Redis String 是可以与 Redis key 关联的最简单的值类型。它是 Memcached 中唯一的数据类型，因此对于新用户来说，在 Redis 中使用 String 是非常自然的。

由于 Redis keys 是字符串，当我们使用字符串类型作为 value 时，我们是在将一个字符串映射到另一个字符串。字符串数据类型在许多场景下都很有用，比如缓存 HTML 片段或页面。

让我们一起通过 redis-cli（在这个指南中所有的例子都会通过 redis-cli 执行）来使用 string 类型。

```shell
> set mykey somevalue
OK
> get mykey
"somevalue"
```

正如你说见，使用 **SET** 和 **GET** 命令是我们设置和获取 string 的 value 的方式。注意，如果 key 已经存在，**SET** 会替代任何已经存储在 key 中的值，即使 key 关联的是一个非 sting 类型的值。因此 **SET** 执行赋值操作。

Values 可以是各种类型的字符串（包括二进制数据），例如，你能将 jpeg 图像存储到 value 中。value 不能超过 512 MB。

**SET** 命令有一些有趣的选项，作为额外的参数提供。例如，我们可以是 **SET** 执行失败当 key 已经存在，相反，也可以让它只有在 key 存在时才能执行成功。

```shell
> set mykey newval nx
(nil)
> set mykey newval xx
OK
```

即使 string 是 Redis 中最基础的类型，你也可以使用它们去执行一些有趣的命令。例如，原子性地增加：

```shell
> set counter 100
OK
> incr counter
(integer) 101
> incr counter
(integer) 102
> incrby counter 50
(integer) 152
```
[INCR]() 命令解析字符串的值作为数字，使其加一，并把最终获取的值设置为新的 value。有很多相似的命令，像 [INCRBY]()，[DECR]() 和 [DECRBY]()。实际上它们都是相同的命令，以略微不同的方式执行。

INCR 是原子性操作是什么意思？即使多个客户端对相同的 key 执行 INCR 命令，也不会相互竞争。例如，在同一时间，客户端 1 和 客户端 2 都读取到 "10"，并都将其增加到 "11"，设置为新值的情况是不会发生的。最终的值一定总是 12，读数-增加-赋值的操作在执行时，其他所有客户端在同一时间都不能执行命令。
