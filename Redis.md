## **名称**数据类型

### string

string 是Redis的最基本的数据类型，可以理解为与 Memcached 一模一样的类型，一个key 对应一个 value。string 类型是二进制安全的，意思是 Redis 的 string 可以包含任何数据，比如图片或者序列化的对象，一个 redis 中字符串 value 最多可以是 512M。

**相关命令**

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180525081907781-1123991256.png)

**自增自减**

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180525081933519-1451227901.png)

**使用场景**

1.缓存

经典使用场景，把常用信息，字符串，图片或者视频等信息放到redis中，redis作为缓存层，mysql做持久化层，降低mysql的读写压力。

2.计数器

redis是单线程模型，一个命令执行完才会执行下一个，同时数据可以一步落地到其他的数据源。

3.session

常见方案spring session + redis实现session共享。

4.限制登录次数

比如登录次数校验，错误超过三次5分钟内就不让登录了，每次登录设置key自增一次，并设置该key的过期时间为5分钟后，每次登录检查一下该key的值来进行限制登录。

### hash

hash 是一个键值对集合，是一个 string 类型的 key和 value 的映射表，key 还是key，但是value是一个键值对（key-value）。类比于 Java里面的 Map<String,Map<String,Object>> 集合。

**相关命令**

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180525082836433-593876169.png)

**使用场景**

缓存

更直观，相比string更节省空间的维护缓存信息，如用户信息，视频信息等。

### list

list 列表，它是简单的字符串列表，按照插入顺序排序，你可以添加一个元素到列表的头部（左边）或者尾部（右边），它的底层实际上是个链表。

列表有两个特点：

- 有序

- 可以重复

**相关命令**

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180525214044910-2026624164.png)

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180525214115346-1562218773.png)

**使用技巧**

一、栈

通过命令 lpush+lpop

二、队列

命令 lpush+rpop

三、有限集合

命令 lpush+ltrim

四、消息队列

命令 lpush+brpop

**使用场景**

timeline

例如微博的时间轴，有人发布微博，用lpush加入时间轴，展示新的列表信息。

### set

集合类型也是用来保存多个字符串的元素，但和列表不同的是集合中

1. 不允许有重复的元素
2. 集合中的元素是无序的，不能通过索引下标获取元素
3. 支持集合间的操作，可以取多个集合取交集、并集、差集

**相关命令**

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180525221025780-633049034.png)

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180525221046544-512036810.png)

**使用场景**

1.标签（tag）

给用户添加标签，或者用户给消息添加标签，这样有同一标签或者类似标签的可以给推荐关注的事或者关注的人。

2.点赞，或点踩，收藏等，可以放到set中实现

### zset

有序集合和集合有着必然的联系，保留了集合不能有重复成员的特性，区别是，有序集合中的元素是可以排序的，它给每个元素设置一个分数，作为排序的依据。

（有序集合中的元素不可以重复，但是score 分数 可以重复，就和一个班里的同学学号不能重复，但考试成绩可以相同）。

**相关命令**

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180525233739895-2031411316.png)

**使用场景**

排行榜

有序集合经典使用场景。例如小说视频等网站需要对用户上传的小说视频做排行榜，榜单可以按照用户关注数，更新时间，字数等打分，做排行。

### stream

Redis的作者在Redis5.0中，放出一个新的数据结构，Stream。

Redis Stream 的内部，其实也是一个队列，每一个不同的key，对应的是不同的队列，每个队列的元素，也就是消息，都有一个msgid，并且需要保证msgid是严格递增的。

在Stream当中，消息是默认持久化的，即便是Redis重启，也能够读取到消息。那么，stream是如何做到多播的呢？

其实非常的简单，与其他队列系统相似，Redis对不同的消费者，也有消费者Group这样的概念，不同的消费组，可以消费同一个消息，对于不同的消费组，都维护一个Idx下标，表示这一个消费群组消费到了哪里，每次进行消费，都会更新一下这个下标，往后面一位进行偏移。



## 底层实现

### 简单动态字符串（simple dynamic string,SDS）

**定义**

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180528075607627-218845583.png)

```c
struct sdshdr{
     //记录buf数组中已使用字节的数量
     //等于 SDS 保存字符串的长度
     int len;
     //记录 buf 数组中未使用字节的数量
     int free;
     //字节数组，用于保存字符串
     char buf[];
}
```

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180527234349672-568401853.png)

**内存重新分配**

C语言由于不记录字符串的长度，所以如果要修改字符串，必须要重新分配内存（先释放再申请），因为如果没有重新分配，字符串长度增大时会造成内存缓冲区溢出，字符串长度减小时会造成内存泄露。

而对于SDS，由于len属性和free属性的存在，对于修改字符串SDS实现了空间预分配和惰性空间释放两种策略：

1、空间预分配：对字符串进行空间扩展的时候，扩展的内存比实际需要的多，这样可以减少连续执行字符串增长操作所需的内存重分配次数。

2、惰性空间释放：对字符串进行缩短操作时，程序不立即使用内存重新分配来回收缩短后多余的字节，而是使用 free 属性将这些字节的数量记录下来，等待后续使用。（当然SDS也提供了相应的API，当我们有需要时，也可以手动释放这些未使用的空间。）



### 链表

**定义**

<img src="https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180528074403440-111834793.png" alt="img" style="zoom:150%;" />

```c
typedef  struct listNode{
       //前置节点
       struct listNode *prev;
       //后置节点
       struct listNode *next;
       //节点的值
       void *value;  
}listNode

typedef struct list{
     //表头节点
     listNode *head;
     //表尾节点
     listNode *tail;
     //链表所包含的节点数量
     unsigned long len;
     //节点值复制函数
     void (*free) (void *ptr);
     //节点值释放函数
     void (*free) (void *ptr);
     //节点值对比函数
     int (*match) (void *ptr,void *key);
}list;
```

**特性**

①、双端：链表具有前置节点和后置节点的引用，获取这两个节点时间复杂度都为O(1)。

②、无环：表头节点的 prev 指针和表尾节点的 next 指针都指向 NULL,对链表的访问都是以 NULL 结束。　　

③、带链表长度计数器：通过 len 属性获取链表长度的时间复杂度为 O(1)。

④、多态：链表节点使用 void* 指针来保存节点值，可以保存各种不同类型的值。



### 字典

字典又称为符号表或者关联数组、或映射（map），是一种用于保存键值对的抽象数据结构。字典中的每一个键 key 都是唯一的，通过 key 可以对值来进行查找或修改。C 语言中没有内置这种数据结构的实现，所以字典依然是 Redis自己构建的。

Redis 的字典使用哈希表作为底层实现。

**定义**

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180528080655703-1600710948.png)

```c
typedef struct dictht{
     //哈希表数组
     dictEntry **table;
     //哈希表大小
     unsigned long size;
     //哈希表大小掩码，用于计算索引值
     //总是等于 size-1
     unsigned long sizemask;
     //该哈希表已有节点的数量
     unsigned long used;
 
}dictht
    
typedef struct dictEntry{
     //键
     void *key;
     //值
     union{
          void *val;
          uint64_tu64;
          int64_ts64;
     }v;
 
     //指向下一个哈希表节点，形成链表
     struct dictEntry *next;
}dictEntry
```

**哈希算法**

```c
#1、使用字典设置的哈希函数，计算键 key 的哈希值
hash = dict->type->hashFunction(key);
#2、使用哈希表的sizemask属性和第一步得到的哈希值，计算索引值
index = hash & dict->ht[x].sizemask;
```

**解决冲突**

链地址法。通过字典里面的 *next 指针指向下一个具有相同索引值的哈希表节点。

**扩容和收缩**

当哈希表保存的键值对太多或者太少时，就要通过 rerehash(重新散列）来对哈希表进行相应的扩展或者收缩。具体步骤：

1、如果执行扩展操作，会基于原哈希表创建一个大小等于 ht[0].used*2n 的哈希表（也就是每次扩展都是根据原哈希表已使用的空间扩大一倍创建另一个哈希表）。相反如果执行的是收缩操作，每次收缩是根据已使用空间缩小一倍创建一个新的哈希表。

2、重新利用上面的哈希算法，计算索引值，然后将键值对放到新的哈希表位置上。

3、所有键值对都迁徙完毕后，释放原哈希表的内存空间。

**扩容条件**

1、服务器目前没有执行 BGSAVE 命令或者 BGREWRITEAOF 命令，并且负载因子大于等于1。

2、服务器目前正在执行 BGSAVE 命令或者 BGREWRITEAOF 命令，并且负载因子大于等于5。

> 负载因子 = 哈希表已保存节点数量 / 哈希表大小。

**渐近式 rehash**

什么叫渐进式 rehash？也就是说扩容和收缩操作不是一次性、集中式完成的，而是分多次、渐进式完成的。

如果保存在Redis中的键值对只有几个几十个，那么 rehash 操作可以瞬间完成，但是如果键值对有几百万，几千万甚至几亿，那么要一次性的进行 rehash，势必会造成Redis一段时间内不能进行别的操作。

所以Redis采用渐进式 rehash,这样在进行渐进式rehash期间，字典的删除查找更新等操作可能会在两个哈希表上进行，第一个哈希表没有找到，就会去第二个哈希表上进行查找。但是进行增加操作，一定是在新的哈希表上进行的。

### 跳跃表

跳跃表（skiplist）是一种有序数据结构，它通过在每个节点中维持多个指向其它节点的指针，从而达到快速访问节点的目的。具有如下性质：

1、由很多层结构组成；

2、每一层都是一个有序的链表，排列顺序为由高层到底层，都至少包含两个链表节点，分别是前面的head节点和后面的nil节点；

3、最底层的链表包含了所有的元素；

4、如果一个元素出现在某一层的链表中，那么在该层之下的链表也全都会出现（上一层的元素是当前层的元素的子集）；

5、链表中的每个节点都包含两个指针，一个指向同一层的下一个链表节点，另一个指向下一层的同一个链表节点；

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180528210921601-949409375.png)

**定义**

```c
typedef struct zskiplistNode {
     //层
     struct zskiplistLevel{
           //前进指针
           struct zskiplistNode *forward;
           //跨度
           unsigned int span;
     }level[];
 
     //后退指针
     struct zskiplistNode *backward;
     //分值
     double score;
     //成员对象
     robj *obj;
 
} zskiplistNode
    
typedef struct zskiplist{
     //表头节点和表尾节点
     structz skiplistNode *header, *tail;
     //表中节点的数量
     unsigned long length;
     //表中层数最大的节点的层数
     int level;
 
}zskiplist;
```

**操作**

①、搜索：从最高层的链表节点开始，如果比当前节点要大和比当前层的下一个节点要小，那么则往下找，也就是和当前层的下一层的节点的下一个节点进行比较，以此类推，一直找到最底层的最后一个节点，如果找到则返回，反之则返回空。

②、插入：首先确定插入的层数，有一种方法是假设抛一枚硬币，如果是正面就累加，直到遇见反面为止，最后记录正面的次数作为插入的层数。当确定插入的层数k后，则需要将新元素插入到从底层到k层。

③、删除：在各个层中找到包含指定值的节点，然后将节点从链表中删除即可，如果删除以后只剩下头尾两个节点，则删除这一层。

**随机level**

**每一个节点的层数（level）是随机出来的**，而且新插入一个节点不会影响其它节点的层数。因此，插入操作只需要修改插入节点前后的指针，而不需要对很多节点都进行调整。这就**降低了插入操作的复杂度**。实际上，这是skiplist的一个很重要的特性，这让它在插入性能上明显优于平衡树的方案。

**比较**

- skiplist和各种平衡树（如AVL、红黑树等）的元素是有序排列的，而哈希表不是有序的。因此，**在哈希表上只能做单个key的查找，不适宜做范围查找。** 所谓范围查找，指的是查找那些大小在指定的两个值之间的所有节点

- 在做范围查找的时候，平衡树比skiplist操作要复杂。在平衡树上，我们找到指定范围的小值之后，还需要以中序遍历的顺序继续寻找其它不超过大值的节点。如果不对平衡树进行一定的改造，这里的中序遍历并不容易实现。而在skiplist上进行范围查找就非常简单，只需要在找到小值之后，对第1层链表进行若干步的遍历就可以实现
- 平衡树的插入和删除操作可能引发子树的调整，逻辑复杂，而**skiplist的插入和删除只需要修改相邻节点的指针**，操作简单又快速
- 从内存占用上来说，skiplist比平衡树更灵活一些。一般来说，平衡树每个节点包含2个指针（分别指向左右子树），而skiplist每个节点包含的指针数目平均为1/(1-p)，具体取决于参数p的大小。如果像Redis里的实现一样，取p=1/4，那么平均每个节点包含1.33个指针，比平衡树更有优势
- 查找单个key，skiplist和平衡树的时间复杂度都为O(log n)，大体相当；而哈希表在保持较低的哈希值冲突概率的前提下，查找时间复杂度接近O(1)，性能更高一些。所以我们平常使用的各种Map或dictionary结构，大都是基于哈希表实现的
- 从算法实现难度上来比较，skiplist比平衡树要简单得多



### 整数集合

整数集合（intset）是Redis用于保存整数值的集合抽象数据类型，它可以保存类型为int16_t、int32_t 或者int64_t 的整数值，并且保证集合中不会出现重复元素。

**定义**

```c
typedef struct intset{
     //编码方式
     uint32_t encoding;
     //集合包含的元素数量
     uint32_t length;
     //保存元素的数组
     int8_t contents[];
 
}intset;
```

整数集合的每个元素都是 contents 数组的一个数据项，它们按照从小到大的顺序排列，并且不包含任何重复项。

length 属性记录了 contents 数组的大小。

需要注意的是虽然 contents 数组声明为 int8_t 类型，但是实际上contents 数组并不保存任何 int8_t 类型的值，其真正类型有 encoding 来决定。

**升级**

当我们新增的元素类型比原集合元素类型的长度要大时，需要对整数集合进行升级，才能将新元素放入整数集合中。具体步骤：

1、根据新元素类型，扩展整数集合底层数组的大小，并为新元素分配空间。

2、将底层数组现有的所有元素都转成与新元素相同类型的元素，并将转换后的元素放到正确的位置，放置过程中，维持整个元素顺序都是有序的。

3、将新元素添加到整数集合中（保证有序）。

升级能极大地节省内存。

**降级**

整数集合不支持降级操作，一旦对数组进行了升级，编码就会一直保持升级后的状态。



### 压缩列表

压缩列表（ziplist）是Redis为了节省内存而开发的，是由一系列特殊编码的连续内存块组成的顺序型数据结构，一个压缩列表可以包含任意多个节点（entry），每个节点可以保存一个字节数组或者一个整数值。

压缩列表的原理：压缩列表并不是对数据利用某种算法进行压缩，而是将数据按照一定规则编码在一块连续的内存区域，目的是节省内存。

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180528215852732-1088896020.png)

**节点构成**

![img](https://images2018.cnblogs.com/blog/1120165/201805/1120165-20180528223605060-899108663.png)

①、previous_entry_ength：记录压缩列表前一个字节的长度。previous_entry_ength的长度可能是1个字节或者是5个字节，如果上一个节点的长度小于254，则该节点只需要一个字节就可以表示前一个节点的长度了，如果前一个节点的长度大于等于254，则previous length的第一个字节为254，后面用四个字节表示当前节点前一个节点的长度。利用此原理即当前节点位置减去上一个节点的长度即得到上一个节点的起始位置，压缩列表可以从尾部向头部遍历。这么做很有效地减少了内存的浪费。

②、encoding：节点的encoding保存的是节点的content的内容类型以及长度，encoding类型一共有两种，一种字节数组一种是整数，encoding区域长度为1字节、2字节或者5字节长。

③、content：content区域用于保存节点的内容，节点内容类型和长度由encoding决定。



## 数据类型实现

[Redis详解（五）------ redis的五大数据类型实现原理 - YSOcean - 博客园 (cnblogs.com)](https://www.cnblogs.com/ysocean/p/9102811.html)



## 内存淘汰



**设置过期时间**

在设置键时设置expire time，也可以在运行时给存在的键设置剩余的生存时间，不设置则默认为-1，设置为-1时表示永久存储。

### 清除过期key

**定期删除**

Redis设定每隔100ms`随机`抽取设置了过期时间的key，并对其进行检查，如果已经过期则删除。

**为什么是随机抽取？** 因为如果存储了大量数据，全部遍历一遍是非常影响性能的！

**惰性删除**

每次获取key时会对key进行判断是否还存活，如果已经过期了则删除。

> Redis中过期的key并不会马上删除，因为定期删除可能正好没抽取到它，我们也没有访问它触发惰性删除



### 内存淘汰

Redis配置文件中可以设置maxmemory，内存的最大使用量，到达限度时会执行`内存淘汰机制`。

|      名称       |                           描述                           |
| :-------------: | :------------------------------------------------------: |
|  volatile-lru   | 从`已设置过期时间`的数据集中挑选`最近最少使用`的数据淘汰 |
|  volatile-lfu   |  从已设置过期时间的数据集中挑选`最不经常`使用的数据淘汰  |
|  volatile-ttl   |    从已设置过期时间的数据集中挑选`将要过期`的数据淘汰    |
| volatile-random |       从已设置过期时间的数据集中挑选`任意数据`淘汰       |
|   allkeys-lru   |       当内存不足写入新数据时淘汰最近最少使用的Key        |
| allkeys-random  |          当内存不足写入新数据时随机选择key淘汰           |
|   allkeys-lfu   |       当内存不足写入新数据时移除最不经常使用的Key        |
|   no-eviction   |  当内存不足写入新数据时，写入操作会报错，同时不删除数据  |

- volatile为前缀的策略都是从已过期的数据集中进行淘汰。
- allkeys为前缀的策略都是面向所有key进行淘汰。
- LRU（least recently used）最近最少用到的。
- LFU（Least Frequently Used）最不常用的。
- 它们的触发条件都是Redis使用的内存达到阈值时。



## 缓存问题

**缓存雪崩**

缓存数据**设置的过期时间相同**，且Redis将这部分数据全部删光了。这就会导致在这段时间内，这些缓存**同时失效**，全部请求到数据库中。

**缓存穿透**

缓存穿透是指查询一个一定**不存在的数据**。由于缓存不命中，这将导致这个不存在的数据**每次请求都要到数据库去查询**，失去了缓存的意义。



## 双写一致性



**缓存主要用于读，数据库用于更新**

- 读的时候，先读缓存，缓存没有读数据库，然后取出数据后放入缓存，同时返回响应。
- 更新的时候
  - 先更新数据库，再删除缓存
  - 缓存设置过期时间，保证最终一致性

**缓存主要用于读取和存储，数据库用于最终存储**

- 读的时候，先查缓存，一般所有需要读取的数据会预加载在缓存中
- 更新的时候，先更新缓存，再异步（可以批量）更新数据库



**最初级的缓存不一致问题及解决方案**

先更新数据库，再删除缓存。如果删除缓存失败了，那么会导致数据库中是新数据，缓存中是旧数据，数据就出现了不一致。

解决思路：

先删除缓存，再更新数据库。如果数据库更新失败了，那么数据库中是旧数据，缓存中是空的，那么数据不会不一致。因为读的时候缓存没有，所以去读了数据库中的旧数据，然后更新到缓存中。



**复杂情况的解决办法**

一个update操作，在删除缓存成功，但update操作未提交的情况下，读请求会读取数据库中旧的值，至此缓存中是旧值，update后的数据库是新值，这种情况就应该采用异步读写请求队列去解决。

简单言之，update请求入队列，读请求入队列，update操作未执行完之前，读操作被阻塞，但是读操作需要while循环 一段时间，因为一旦当前操作的读请求之前还有一个读请求在队列中，很可能前一个读请求已经将update后的新值已经读取到redis当中了。

 一般来说，如果允许缓存可以稍微的跟数据库偶尔有不一致的情况，也就是说如果你的系统不是严格要求 “缓存+数据库” **必须保持一致性**的话，最好不要做这个方案，即：**读请求和写请求串行化，串到一个内存队列里去**。

串行化可以保证一定不会出现不一致的情况，但是它也会导致系统的吞吐量大幅度降低，用比正常情况下多几倍的机器去支撑线上的一个请求。



**缓存和数据库一致性解决方案**

1. **延时双删**

在写库前后都进行redis.del(key)操作，并且设定合理的超时时间。

```
//伪代码
redis.delKey( key );
db.updateData( data );
Thread.sleep( time_sleep );
redis.delKey( key );
```

time_sleep为休眠时间，需要评估自己的项目的读数据业务逻辑的耗时。这么做的目的，就是确保读请求结束，写请求可以删除读请求造成的缓存脏数据。

当然这种策略还要考虑redis和数据库主从同步的耗时。最后的的写数据的休眠时间：则在读数据业务逻辑的耗时基础上，加几百ms即可。比如：休眠1秒。

**缓存过期时间**

从理论上来说，给缓存设置过期时间，是保证最终一致性的解决方案。所有的写操作以数据库为准，只要到达缓存过期时间，则后面的读请求自然会从数据库中读取新值然后回填缓存。

**弊端**

结合双删策略+缓存超时设置，这样最差的情况就是在超时时间内数据存在不一致，而且又增加了写请求的耗时。



2.**异步更新缓存**

MySQL binlog增量订阅消费+消息队列+增量数据更新到redis

- 读Redis：热数据基本都在Redis
- 写MySQL:增删改都是操作MySQL
- 更新Redis数据：MySQ的数据操作binlog，来更新到Redis

**Redis更新**

(1）数据操作主要分为两大块：

- 一个是全量(将全部数据一次写入到redis)
- 一个是增量（实时更新）

这里说的是增量,指的是mysql的update、insert、delate变更数据。

(2）读取binlog后分析 ，利用消息队列,推送更新各台的redis缓存数据。

这样一旦MySQL中产生了新的写入、更新、删除等操作，就可以把binlog相关的消息推送至Redis，Redis再根据binlog中的记录，对Redis进行更新。

其实这种机制，很类似MySQL的主从备份机制，因为MySQL的主备也是通过binlog来实现的数据一致性。


