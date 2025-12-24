- 键值数据库

# NoSQL

- 非关系型数据库
- 非结构化
- 无关联的
- 非SQL
- 事务特性BASE

<img src="D:\refines\refines\reids1.png" alt="reids1" style="zoom: 50%;" />

# Redis

- Redis诞生于2009年全称是`Re`mote`Di`ctionary`S`erver，`远程词典服务器`，是一个基于`内存`的`键值型``NoSQL数据库`。
- 特征
  1. 键值（key-value）型，value支持多种不同数据结构，功能丰富
  2. 单线程，每个命令具备原子性
  3. 低延迟，速度快（基于内存、I0多路复用、良好的编码）
  4. 支持数据持久化
  5. 支持主从集群、分片集群
  6. 支持多语言客户端
- Redis是一个key-value的数据库，key一般是String类型，不过value的类型多种多样：
  <img src="D:\refines\refines\redis2.png" alt="redis2" style="zoom:67%;" />

---

## 通用命令

1. `KEYS`：查看符合模板的所有KEY
2. `DEL`：删除指定的KEY
3. `EXISTS`：判断key是否存在
4. `EXPIRE`：一个key设置有效期，有效期到期时该key会被自动删除
5. `TTL`：查看一个key的剩余有效期
   1. `-1`：永久有效
   2. `-2`：已失效

---

## 数据结构

### String

- String类型，也就是字符串类型，是Redis中最简单的存储类型。
  其value是字符串，不过根据字符串的格式不同，又可以分为3类：
  1. string:普通字符串
  2. int：整数类型，可以做自增、自减操作
  3. float：浮点类型，可以做自增、自减操作
- String的常见命令有：
  1. `SET`：`添加或者修改``已经存在`的一个String类型的键值对
  2. `GET`：根据key`获取`String类型的value
  3. `MSET`：`批量添加`多个String类型的键值对
  4. `MGET`：根据多个key`获取多个`String类型的value
  5. `INCR`：让一个整型的key`自增1`
  6. `INCRBY`:让一个整型的key`自增并指定步长`，例如：incrby num 2让num值自增2
  7. `INCRBYFLOAT`：让一个`浮点`类型的数字`自增并指定步长`
  8. `SETNX`：`添加一个`String类型的键值对，前提是这个key不存在，否则不执行
  9. `SETEX`：`添加一个`String类型的键值对，并且`指定有效期`

### Keys层级格式

- Redis的key允许有多个单词形成层级结构，多个单词之间用'：隔开，格式如下：

  ```redis
  项目名:业务名:类型:id
  ```

- e.g

  ```sql
  set heima:user:2 '{"id":2, "name":"tim", "age":21}'
  ```

---

### Hash

- Hash类型，也叫散列，其value是一个无序字典，类似于Java中的HashMap结构。
- Hash结构可以将对象中的每个字段独立存储，可以针对单个字段做CRUD：
  <img src="D:\refines\refines\redis3.png" alt="redis3" style="zoom:67%;" />

#### 常见命令

- `HSETkeyfieldvalue`：添加或者修改hash类型key的field的值
- `HGETkeyfield`：获取一个hash类型key的field的值
- `HMSET`：批量添加多个hash类型key的field的值
- `HMGET`：批量获取多个hash类型key的field的值
- `HGETALL`：获取一个hash类型的key中的所有的field和value
- `HKEYS`：获取一个hash类型的key中的所有的field
- `HVALS`：获取一个hash类型的key中的所有的value
- `HINCRBY`：让一个hash类型key的字段值自增并指定步长
- `HSETNX`：添加一个hash类型的key的field值，前提是这个field不存在，否则不执行

---

### List

- Redis中的List类型与Java中的LinkedList类似，可以看做是一个双向链表结构。既可以支持正向检索和也可以支持反向
  检索。
- 特征
  1. 有序
  2. 元素可以重复
  3. 插入和删除快
  4. 查询速度一般

#### 常见命令

- `LPUSH key element`...：向列表`左侧插入`一个或多个元素
- `LPOP key`：`移除并返回`列表`左侧的第一个`元素，没有则返回nil
- `RPUSH key element`...：向列表`右侧插入`一个或多个元素
- `RPOP key`：`移除并返回`列表`右侧的第一个`元素
- `LRANGE key star end`：返回一段`角标范围内`的`所有元素`
- `BLPOP`和`BRPOP`：与LPOP和RPOP类似，只不过在没有元素时`等待指定时间`，而不是直接返回nil

---

### Set

- Redis的Set结构与Java中的HashSet类似，可以看做是一个value为null的HashMap。因为也是一个hash表，因此具备
  与HashSet类似的特征：
- 特征
  1. 无序
  2. 元素不可重复
  3. 查找快
  4. 支持交集、并集、差集等功能

#### 常见命令

- `SADD key member...`：向set中添加一个或多个元素
- `SREM key member...`：移除set中的指定元素
- `SCARD key`:返回set中元素的个数
- `SISMEMBER key member`：判断一个元素是否存在于set中
- `SMEMBERS`：获取set中的所有元素
- `SINTER key1 key2..`：求key1与key2的交集
- `SDIFF key1 key2..`：求key1与key2的差集
- `SUNlON key1 key2`..：求key1和key2的并集

---

### SortedSet

- Redis的SortedSet是一个`可排序`的`set集合`，与Java中的TreeSet有些类似，但底层数据结构却差别很大。SortedSet中的每一个元素都带有一个score属性，可以基于score属性对元素排序，底层的实现是一个`跳表`（SkipList）加`hash表`。SortedSet具备下列特性：
  1. 可排序
  2. 元素不重复
  3. 查询速度快
- 因为`SortedSet`的可排序特性，经常被用来实现排行榜这样的功能。

#### 常见命令

- `ZADD key score member`：`添加`一个或多个元素到sorted set，如果已经存在则`更新`其score值
- `ZREM key member`：`删除`sorted set中的一个指定元素
- `ZSCORE key member`：`获取`sorted set中的指定元素的score值
- `ZRANK key member`：`获取`sortedset中的指定元素的`排名`
- `ZCARD key`：获取sortedset中的`元素个数`
- `ZCOUNT key min max`：统计score值在`给定范围内`的所有元素的`个数`
- `ZINCRBY key increment member`：让sorted set中的指定元素`自增`，`步长为指定`的increment值
- `ZRANGE key min max`：按照score排序后，获取指定`排名范围内的元素`
- `ZRANGEBYSCORE key min max`：按照score排序后，获取指定`score范围内的元素`
- `ZDIFF`、`ZINTER`、`ZUNION`：求差集、交集、并集
- 注意：所有的排名默认都是升序，如果要降序则在命令的Z后面添加REV即可

## Redis的Java客户端

1. `Jedis`
   - 以Redis命令作为方法名称，学习成本低，简单实用
     但是Jedis实例是线程不安全的，多线程环境下需要基
     于连接池来使用
2. `lettuce`
   - Lettuce是基于Netty实现的，支持同步、异步和响
     应式编程方式，并且是线程安全的。支持Redis的哨兵
     模式、集群模式和管道模式。
3. `redisson`
   - Redisson是一个基于Redis实现的分布式、可伸缩的
     Java数据结构集合。包含了诸如Map、Queue、Lock、
     Semaphore、AtomicLong等强大功能

### Jedis

#### 连接池

- Jedis本身是线程不安全的，并且频繁的创建和销毁连接会有性能损耗，因此我们推荐大家使用Jedis连接池代替ledis的直连方式

<img src="D:\refines\refines\redis4.png" alt="redis4" style="zoom: 50%;" />

### Spring Data Redis

- SpringData是Spring中`数据操作`的`模块`，包含对各种`数据库的集成`，其中对Redis的`集成模块`就叫做`SpringDataRedis`
- 提供了对不同Redis客户端的整合（Lettuce和Jedis）
- 提供了RedisTemplate`统一APl`来操作Redis
- 支持Redis的`发布订阅模型`
- 支持Redis`哨兵`和Redis`集群`
- 支持基于`Lettuce`的`响应式编程`
- 支持基于JDK、JSON、字符串、Spring对象的`数据序列化及反序列化`
- 支持基于Redis的`JDKCollection`实现

- SpringDataRedis中提供了RedisTemplate工具类，其中封装了各种对Redis的操作。并且将不同数据类型的操作APl封装到了不同的类型中：![redis5](D:\refines\refines\redis5.png)

#### 序列化方式

​		RedisTemplate可以接收任意Object作为值写入Redis，只不过写入前会把object序列化为字节形式，默认是采用JDK
序列化，得到的结果是这样的：![redis6](D:\refines\refines\redis6.png)

- 缺点
  1. 可读性差
  2. 内存占用较大
