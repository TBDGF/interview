## 面向对象

[了解面向对象的特性，了解重载、重写等机制-美团面试基本题 - aspirant - 博客园 (cnblogs.com)](https://www.cnblogs.com/aspirant/p/10762422.html)

**面向对象的优点**

- 提高了代码的可扩展性。
- 提高了代码的可维护性。
- 面向对象的封装，继承，多态。



**面向对象的特征**

- 封装：封装是把对象的属性和实现细节隐藏起来，仅对外提供公共的访问方法（这些对象通过一个受保护的接口访问其他对象）。

- 继承：多个类中存在相同的属性和行为时，将这些相同的内容抽取到一个单独的类中，那么多个类无需再定义这些属性和行为，只要继承这个类即可，继承这个类的为新类，新类称为原始类的派生类（子类）而原始类称为新类的基类（父类）。派生类可以从它的基类哪里继承方法和实例变量，并且类可以修改或增加新的方法使之更适合特殊的需要。可通过extends关键字实现继承。

- 多态：多态性是指允许不同类的对象对同一消息作出响应，多态性语言具有灵活，抽象，行为共享，代码共享的优势，很好解决了应用程序函数同名的问题。

  例子：可以将 ArrayList 或 LinkedList 实例化到 List 对象上并操作。



**如何理解面向对象**

世间万物皆对象，对象有具体的的实例化，任何方法或者属性都要写在对象(类)里面，就是不断的创建对象使用对象指挥对象做事。



**继承和多态的区别**

继承是子类获得父类的成员，重写是继承后重新实现父类的方法。重载是在一个类里一系列 参数不同 名字相同 的方法。

多态则是为了避免在父类里大量重载引起代码臃肿且难于维护。

> 继承是子类使用父类的方法，而多态则是父类使用子类的方法。



**类的组成和执行顺序**

- 类的组成：属性 方法 静态块 非静态块。
- 执行顺序：父类，子类，静态块，静态字段，非静态块，非静态字段，构造器，方法。



**构造方法可否能被重写**

不能被重写，只有继承关系才能重写，构造方法不能被重写，但是能被重载



**多态的实现方式**

多态必要的条件：继承、父类的引用指向子类的对象。

重写，接口，抽象类



**final**

final 关键字可以修饰类、方法和属性。

- 当 final 修饰类的时候，这个类不能被继承。final 类中的所有成员方法都会被隐式地指定为 final 方法。

- 当 final 修饰方法的时候，表明这个方法不能被重写。

- 当 final 修饰属性的时候，如果是基本数据类型的变量，其数值在初始化之后便不能更改。如果是引用类型的变量，则在对其初始化之后便不能再让其指向另一个对象。





### 接口与抽象类

[Java抽象类与接口的区别 - aspirant - 博客园 (cnblogs.com)](https://www.cnblogs.com/aspirant/p/7079670.html)

| **参数**           | **抽象类**                                                   | **接口**                                                     |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **默认的方法实现** | **它可以有默认的方法实现**                                   | **接口完全是抽象的。它根本不存在方法的实现**                 |
| 实现               | 子类使用**extends**关键字来继承抽象类。如果子类不是抽象类的话，它需要提供抽象类中所有声明的方法的实现。 | 子类使用关键字**implements**来实现接口。它需要提供接口中所有声明的方法的实现 |
| 构造器             | 抽象类可以有构造器                                           | 接口不能有构造器                                             |
| 与正常Java类的区别 | 除了你不能实例化抽象类之外，它和普通Java类没有任何区别       | 接口是完全不同的类型                                         |
| **访问修饰符**     | **抽象方法可以有public、protected和default这些修饰符**       | **接口方法默认修饰符是public。你不可以使用其它修饰符。**     |
| main方法           | 抽象方法可以有main方法并且我们可以运行它                     | 接口没有main方法，因此我们不能运行它。                       |
| 多继承             | 抽象方法可以继承一个类和实现多个接口                         | 接口只可以继承一个或多个其它接口                             |
| 速度               | 它比接口速度要快                                             | 接口是稍微有点慢的，因为它需要时间去寻找在类中实现的方法。   |
| **添加新方法**     | **如果你往抽象类中添加新的方法，你可以给它提供默认的实现。因此你不需要改变你现在的代码。** | **如果你往接口中添加方法，那么你必须改变实现该接口的类。**   |

- 抽象类使用abstract修饰 ，接口使用interface修饰。
- 抽象类可以有普通方法，接口不可有有普通方法只能有抽象方法。
- 抽象类可以有普通属性，接口只能是常量。
- 抽象类和接口不能实例化，就是不能new，也就是不能创建对象，因为不是具体的。
- 抽象类有构造方法，接口没有构造方法。
- 抽象类只支持单继承支持多实现，接口支持多继承。



**什么时候使用抽象类和接口**

- 如果你拥有一些方法并且想让它们中的一些有默认实现，那么使用抽象类吧。
- 如果你想实现多重继承，那么你必须使用接口。由于**Java不支持多继承**，子类不能够继承多个类，但可以实现多个接口。因此你就可以使用接口来解决它。
- 如果基本功能在不断改变，那么就需要使用抽象类。如果不断改变基本功能并且使用接口，那么就需要改变所有实现了该接口的类。



### 访问修饰符

类的访问修饰符有：public、缺省

- public：Java 语言中类的可访问控制符只有一个： public 即公共的。每个 Java 程序的主类都必须是 public 类作为公共工具。
- 缺省：如果一个类没有访问控制符，说明它具有缺省的访问控制符特性。此时，这个类只能被同一个包中的类访问或引用。

属性和方法的访问修饰符有：public、private、protected、缺省

- public：如果属于一个公共类，则可以被所有其它类所引用。
- private：只能被该类自身所访问，而不能被任何其它类 ( 包括子类 ) 所引用。
- protected：可以被三种类所引用：①该类自身；②与它在同一个包中的其它类；③子类。
- 缺省：若没有声明任何访问修饰符，可被同一包中的其它类访问。

![img](https://iknow-pic.cdn.bcebos.com/cdbf6c81800a19d865fd770a3efa828ba71e46c7?x-bce-process%3Dimage%2Fresize%2Cm_lfit%2Cw_600%2Ch_800%2Climit_1%2Fquality%2Cq_85%2Fformat%2Cf_jpg)









## 重载和重写

[深入理解Java中方法重载的实现原理 - 特务依昂 - 博客园 (cnblogs.com)](https://www.cnblogs.com/tuyang1129/p/12519578.html)

### 为什么返回值不同不能重载

`Java`中的每一个方法，都有自己的签名，或者也可以叫做标识，用来确认它的唯一性。**在同一个类中，不能出现两个签名一样的方法**。而方法的签名由什么组成呢？答案是**方法名称 + 参数列表**，也就是说，一个类中不允许出现两个方法名称一样，而且方法的参数列表也一样的方法（一个`static`，一个非`static`也不行）。知道上面的概念后，我们就可以定义方法重载了：**在同一个类中，拥有相同方法名称，但是不同参数列表的多个方法，被称为重载方法，这种形式被称为方法的重载**。

因为我们调用方法时，并不一定需要接收方法的返回值，这时编译器就无法判断。



## 数据类型

**基本数据类型**

Byte（字节型）：1

short（短整型）：2

char（字符型） ：2

int（整型）：4

float（单精度型/浮点型）：

long（长整型）：8

double（双精度型） ：8

boolean(布尔类型）：1

**引用数据类型**

除了基本的数据类型，其他都是引用数据类型。



**区别**

- 基本类型只能按值传递，封装类按引用传递
- 基本类型在堆栈上分配，对象在堆上分配（对象的引用在堆栈上创建）
  - 基本类型的局部变量在栈上分配，对象的成员变量在堆上分配
- 封装类可以更方便的使用一些基本类型不具备的方法



**==和equals**

- ==
  - 对于基本数类型，== 比较值
  - 对于引用数据类型， == 比较内存地址
- equals
  - 没有重写 equals 时，使用 == 比较地址
  - 可以重写为比较值



## static

被static静态修饰的成员方法，成员变量，成员内部类都是随着类文件的加载而加载到方法区中，且只加载一次。如果需要调用，直接用类名去调用。

用途是在不创建对象的情况下调用变量和方法。

**静态方法**

在静态方法中不能访问非静态的成员方法和成员变量，但是在非静态成员方法中是可以访问静态成员方法/变量的。

**静态变量**

静态变量被所有的对象所共享，在内存中只有一个副本，它当且仅当在类初次加载时会被初始化。而非静态变量是对象所拥有的，在创建对象的时候被初始化，存在多个副本，各个对象拥有的副本互不影响。

**静态内部类**

java的内部类并不一定要要声明成static。

如果不是static的内部类，必须依赖外部类的实例才能生成。

如果是static的，则无须依赖外部类。



## hashCode 和 equals

**1、equals()既然已经能实现对比的功能了，为什么还要hashCode()呢？**

因为重写的equals（）里一般比较的比较全面比较复杂，这样效率就比较低，而利用hashCode()进行对比，则只要生成一个hash值进行比较就可以了，效率很高。

**2、hashCode()既然效率这么高为什么还要equals()呢？**

因为hashCode()并不是完全可靠，有时候不同的对象他们生成的hashcode也会一样（生成hash值得公式可能存在的问题），所以hashCode()只能说是大部分时候可靠，并不是绝对可靠，所以我们可以得出（PS：以下两条结论是重点，很多人面试的时候都说不出来）：

- equals()相等的两个对象他们的hashCode()肯定相等，也就是用equals()对比是绝对可靠的。
- hashCode()相等的两个对象他们的equals()不一定相等，也就是hashCode()不是绝对可靠的。

**扩展**

- 只要重写 equals，就必须重写 hashCode；
- 因为 Set 存储的是不重复的对象，依据 hashCode 和 equals 进行判断，所以 Set 存储的对象必须重写这两个方法；
- 如果自定义对象做为 Map 的键，那么必须重写 hashCode 和 equals；
- String 重写了 hashCode 和 equals 方法，所以我们可以非常愉快地使用 String 对象作为 key 来使用；



## 集合



### 集合间的继承关系

![img](https://img-blog.csdnimg.cn/20190514164943406.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zNjM3ODkxNw==,size_16,color_FFFFFF,t_70)





### ArrayList

#### 和 Array 区别

1：数组是定长，list是自动增长。

2：数组效率高，list效率低。

总结：数组牺牲功能增加效率，list牺牲效率增加功能。



基于动态数组。

如果我们要在某一个位置添加或者删除一个元素，剩下的每个元素都要相应地依次复制插入到后面一格。

插入，删除，查找，扩容的复杂度都是 O(n)。

#### 线程不安全

对ArrayList进行添加元素的操作的时候是分两个步骤进行的，即第一步先在object[size]的位置上存放需要添加的元素；第二步将size的值增加1。由于这个过程在多线程的环境下是不能保证具有原子性的，因此ArrayList在多线程的环境下是线程不安全的。

#### 扩容

ArrayList的扩容主要发生在向ArrayList集合中添加元素的时候。由add()方法的分析可知添加前必须确保集合的容量能够放下添加的元素。主要经历了以下几个阶段：

第一，在add()方法中调用ensureCapacityInternal(size + 1)方法来确定集合确保添加元素成功的最小集合容量minCapacity的值。参数为size+1，代表的含义是如果集合添加元素成功后，集合中的实际元素个数。换句话说，集合为了确保添加元素成功，那么集合的最小容量minCapacity应该是size+1。在ensureCapacityInternal方法中，首先判断elementData是否为默认的空数组，如果是，minCapacity为minCapacity与集合默认容量大小中的较大值。

第二，调用ensureExplicitCapacity(minCapacity)方法来确定集合为了确保添加元素成功是否需要对现有的元素数组进行扩容。首先将结构性修改计数器加一；然后判断minCapacity与当前元素数组的长度的大小，如果minCapacity比当前元素数组的长度的大小大的时候需要扩容，进入第三阶段。

第三，如果需要对现有的元素数组进行扩容，则调用grow(minCapacity)方法，参数minCapacity表示集合为了确保添加元素成功的最小容量。在扩容的时候，首先将原元素数组的长度增大1.5倍（oldCapacity + (oldCapacity >> 1)），然后对扩容后的容量与minCapacity进行比较：① 新容量小于minCapacity，则将新容量设为minCapacity；②新容量大于minCapacity，则指定新容量。最后将旧数组拷贝到扩容后的新数组中。



#### 优缺点

**优点**

1. ArrayList底层以数组实现，是一种随机访问模式，再加上它实现了RandomAccess接口，因此查找也就是get的时候非常快。
2. ArrayList在顺序添加一个元素的时候非常方便，只是往数组里面添加了一个元素而已。
3. 根据下标访问元素，效率高。
4. 可以自动扩容，默认为每次扩容为原来的1.5倍。

**缺点**

1. 插入和删除元素的效率不高。
2. 根据元素查找下标需要遍历整个元素数组，效率不高。
3. 线程不安全。



### LinkedList

基于双向链表。





### HashSet

- 是基于HashMap实现的，默认构造函数是构建一个初始容量为16，负载因子为0.75 的HashMap。封装了一个 HashMap 对象来存储所有的集合元素，所有放入 HashSet 中的集合元素实际上由 HashMap 的 key 来保存，而 HashMap 的 value 则存储了一个 PRESENT，它是一个静态的 Object 对象。
- 当我们试图把某个类的对象当成 HashMap的 key，或试图将这个类的对象放入 HashSet 中保存时，重写该类的equals(Object obj)方法和 hashCode() 方法很重要，而且这两个方法的返回值必须保持一致：当该类的两个的 hashCode() 返回值相同时，它们通过 equals() 方法比较也应该返回 true。通常来说，所有参与计算 hashCode() 返回值的关键属性，都应该用于作为 equals() 比较的标准。
- HashSet的其他操作都是基于HashMap的。



### HashMap

[图解 HashMap 源码——逐行分析源码，面试再也不怕被问HashMap了_every__day的博客-CSDN博客](https://blog.csdn.net/every__day/article/details/114118922)

在JDK1.6，JDK1.7中，HashMap采用位桶+链表实现，即使用链表处理冲突，同一hash值的链表都存储在一个链表里。但是当位于一个桶中的元素较多，即hash值相等的元素较多时，通过key值依次查找的效率较低。

而JDK1.8中，HashMap采用位桶+链表+红黑树实现，当数组长度大于等于64，且链表长度大于8，将链表转换为红黑树，这样大大减少了查找时间。

首先有一个数组，当添加一个元素（key-value）时，就首先计算元素key的hash值，以此确定插入数组中的位置，但是可能存在同一hash值的元素已经被放在数组同一位置了，这时就添加到同一hash值的元素的后面，他们在数组的同一位置，但是形成了链表，同一各链表上的Hash值是相同的，所以说数组存放的是链表。而当链表长度太长时，链表就转换为红黑树，这样大大提高了查找的效率。



#### hash

```java
//拿到对象的 hashCode
h = hashCode();
//将 hashCode 右移 16 位，让 hashCode 的高位与地位异或，增加低位的随机性。并且混合后的值也变相保持了高位的特征。
hash = h ^ (h >>> 16);
//只取前几位的 hash 作为 index
index = hash & (arrays.length-1);
```



**为什么不直接用红黑树**

红黑树平均查找长度是 log(n) ，链表平均查找长度是 n/2 。

当 n<8 时，平均查找长度相近，但是红黑树的插入删除时的旋转开销都较大，节点占用的空间较大。所以选择使用链表。

当 n>8 时，平均查找长度有了较显著的差别，这时转化为树才有了意义。

所以说这种策略也是一种时间和空间上的妥协。



#### 扩容

即当前元素数量超过数组的长度乘以加载因子（默认0.75）的值的时候，就要自动扩容。

初始化后首次插入数据时，先发生 resize 扩容再插入数据。之后每当插入的数据到达阈值时就会发生 resize ，这时是先插入数据再 resize 。

![img](https://img-blog.csdn.net/20170123110716285)

扩容时，遍历 hashmap 每个 bucket 里的链表，每个链表可能会被拆分成两个链表，不需要移动的元素置入 loHead 为首的链表，需要移动的元素置入 hiHead为首的链表，然后分别分配给老的buket（原索引）和新的buket（原索引+oldCap） 。



扩容时，如果节点是红黑树节点，就会调用TreeNode的split方法对当前节点作为跟节点的红黑树进行修剪。HashMap 扩容时对红黑树节点的修剪主要分两部分，先分类、再根据元素个数决定是还原成链表还是精简一下元素仍保留红黑树结构。

1.分类

指定位置、指定范围，让指定位置中的元素 `（hash & bit) == 0` 的，放到 lXXX 树中，不相等的放到 hXXX 树中。

2.根据元素个数决定处理情况

符合要求的元素（即 lXXX 树），在元素个数小于等于 6 时还原成链表，最后让哈希表中修剪的痛 tab[index] 指向 lXXX 树；在元素个数大于 6 时，还是用红黑树，只不过是修剪了下枝叶；

不符合要求的元素（即 hXXX 树）也是一样的操作，只不过最后它是放在了修剪范围外 tab[index + bit]。



**为什么不使用 AVL 树**

AVL 树是平衡树，在查找时效率比红黑树高一点。

红黑树是近似平衡的树，在维护平衡的成本上，要比AVL树要低。

所以红黑树的插入、删除、查找等各种操作的性能都比较稳定。



#### 线程不安全

[HashMap多线程并发问题分析-正常和异常的rehash1(阿里) - aspirant - 博客园 (cnblogs.com)](https://www.cnblogs.com/aspirant/p/11504389.html)

HashMap 的线程不安全最主要是体现在扩容和插入中，这里又分为 JDK7 和 JDK8 两种情况。

**JDK7**

JDK7 中节点插入采用头插法

- 在扩容中：假设线程1在遍历过程中，拿到了下一次准备遍历的next，这时线程2也在扩容，会修改next对象。当线程1继续执行时，可能会造成两个Entry互相引用，造成**死循环**，并且**丢失元素**。
- 在插入中：假设两个线程同时拿到链表头，第一个链表插入后，第二个链表的插入就会覆盖第一个链表的操作，造成**元素覆盖**。

**JDK8**

JDK8 中节点插入采用尾插法，避免了链表成环，造成死循环。

- 插入中：会造成**元素覆盖**。



### HashTable

HashTable 无论 key 还是 value 都不能为 null。

Hashtable是线程安全的，多个线程可以共享一个Hashtable。

实现线程安全的方式是在修改数据时锁住整个Hashtable，效率低。



### ConcurrentHashMap

[java-并发-ConcurrentHashMap高并发机制-jdk1.8_阿里Darker-CSDN博客](https://blog.csdn.net/jianghuxiaojin/article/details/52006118)

[图解 ConCurrentHashMap ——从源码层面，弄清楚它是怎么控制并发的_every__day的博客-CSDN博客](https://blog.csdn.net/every__day/article/details/114293107)

[ConCurrentHashMap并发环境时，如何计数的？—— sumCount()、fullAddCount()_every__day的博客-CSDN博客_concurrenthashmap计数](https://blog.csdn.net/every__day/article/details/115030000)

ConcurrentHashMap 1.8 采用Node + CAS + Synchronized来保证并发安全进行实现，采用table数组＋链表＋红黑树的存储结构。以table数组元素作为锁，利用CAS+Synchronized来保证并发更新的安全，从而实现了对每个数组元素（Node）进行加锁，进一步减少并发冲突的概率。ConcurrentHashMap可以做到读取数据不加锁，并且其内部的结构可以让其在进行写操作的时候能够将锁的粒度保持地尽量地小，允许多个修改操作并发进行。

<img src="https://img-blog.csdnimg.cn/20200409211332776.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzMjUzMTIz,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述"  />



#### 区别

- key 和 value 均不能为空



#### 内部类



**Node**

Node 是最核心的内部类，它包装了 key-value 键值对，所有插入 ConcurrentHashMap 的数据都包装在这里面。

- 这个 Node 内部类与 HashMap 中定义的 Node 类很相似，但是有一些差别，
- 它对 value 和 next 属性设置了 **volatile** 同步锁 
- 它不允许调用 setValue 方法直接改变 Node 的 value 域 
- 它增加了 find 方法辅助 map.get() 方法 



**TreeNode**

树节点类，另外一个核心的数据结构。当链表长度过长的时候，会转换为 TreeNode。但是与 HashMap 不相同的是，它并不是直接转换为红黑树，而是把这些结点包装成 TreeNode 放在 TreeBin 对象中，由 TreeBin 完成对红黑树的包装。

而且 TreeNode 在 ConcurrentHashMap 集成自 Node 类，而并非 HashMap 中的集成自 LinkedHashMap.Entry<K,V> 类，也就是说 TreeNode 带有 next 指针，这样做的目的是方便基于 TreeBin 的访问。



**TreeBin**

这个类并不负责包装用户的 key、value 信息，而是包装的很多 TreeNode 节点。它代替了TreeNode 的根节点，也就是说在实际的 ConcurrentHashMap “数组” 中，存放的是 TreeBin 对象，而不是 TreeNode 对象，这是与 HashMap 的区别。另外这个类还带有了读写锁。

这里仅贴出它的构造方法。可以看到在构造 TreeBin 节点时，仅仅指定了它的 hash 值为 TREEBIN 常量，这也就是个标识为。同时也看到我们熟悉的红黑树构造方法。



**ForwardingNode**

一个用于连接两个 table 的节点类。它包含一个 nextTable 指针，用于指向下一张表。而且这个节点的 key value next 指针全部为 null，它的 hash 值为 -1。这里面定义的 find 的方法是从 nextTable 里进行查询节点，而不是以自身为头节点进行查找



#### CAS

JDK8中ConcurrentHashMap参考了JDK8 HashMap的实现，采用了数组+链表+红黑树的实现方式来设计，内部大量采用CAS操作。

CAS是compare and swap的缩写，即我们所说的比较交换。cas是一种基于锁的操作，而且是乐观锁。

乐观锁总是假设最好的情况，每次去拿数据的时候都认为别人不会修改，所以不会上锁，但是在更新的时候会判断一下在此期间别人有没有去更新这个数据，可以使用版本号机制和CAS算法实现。乐观锁适用于多读的应用类型，这样可以提高吞吐量。

CAS 操作包含三个操作数 —— 内存位置（V）、预期原值（A）和新值(B)。如果内存地址里面的值和A的值是一样的，那么就将内存里面的值更新成B。CAS是通过自旋来获取数据的，若果在第一轮循环中，a线程获取地址里面的值被b线程修改了，那么a线程需要自旋，到下次循环才有可能机会执行。



#### 计数

对于 ConcurrentHashMap 来说，这个 table 里到底装了多少东西其实是个不确定的数量，因为不可能在调用 size() 方法的时候像 GC 的 “stop the world” 一样让其他线程都停下来让你去统计，因此只能说这个数量是个估计值。对于这个估计值，ConcurrentHashMap 也是大费周章才计算出来的。

计数的方法有 size 和 mappingSize，而这两个方法都是调用 sumCount 方法。

- size 返回 int，是将 long 强转为 int
- mappingSize 返回 long，可计数的范围更大

sumCount 统计 baseCount 和各个 CounterCell 的和。

```java
final long sumCount() {                      
    CounterCell[] as = counterCells;         
    CounterCell a;                           
    long sum = baseCount;                    
    if (as != null) {                        
        for (int i = 0; i < as.length; ++i) {
            if ((a = as[i]) != null)         
                sum += a.value;              
        }                                    
    }                                        
    return sum;                              
}                                            
```



计数时，要么修改了 `baseCount`，要么 修改了 `CounterCell` 对象中 `value` 的值。

在 put 和 remove 中，都调用了 addCount 这个方法。这个的一个重要功能就是计数。

#### 总结

- 无竞争条件下，执行 put() 方法时，操作 baseCount 实现计数
- 首次竞争条件下，执行 put() 方法，会初始化 CounterCell ，并实现计数
- CounterCell 一旦初始化，计数就优先使用 CounterCell
- 每个线程，要么修改 CounterCell、要么修改 baseCount，实现计数
- CounterCell 在竞争特别严重时，会扩容。（扩容上限与 CPU 核数有关，不会一直扩容）







## 泛型

**1. Java中的泛型是什么 ? 使用泛型的好处是什么?**

这是在各种Java泛型面试中，一开场你就会被问到的问题中的一个，主要集中在初级和中级面试中。那些拥有Java1.4或更早版本的开发背景的人都知道，[在集合中存储对象](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fjavarevisited.blogspot.com%2F2012%2F07%2Fcreate-read-only-list-map-set-example-java.html)并在使用前进行类型转换是多么的不方便。泛型防止了那种情况的发生。它提供了编译期的类型安全，确保你只能把正确类型的对象放入集合中，避免了在运行时出现ClassCastException。

 

**2. Java的泛型是如何工作的 ? 什么是类型擦除 ?**

这是一道更好的泛型面试题。泛型是通过**类型擦除**来实现的，编译器在编译时擦除了所有类型相关的信息，所以在运行时不存在任何类型相关的信息。例如List<String>在运行时仅用一个[List](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fwww.blogger.com%2Fgoog_1304192070)来表示。这样做的目的，是确保能和Java 5之前的版本开发二进制类库进行兼容。你无法在运行时访问到类型参数，因为编译器已经把**泛型类型**转换成了**原始类型**。根据你对这个泛型问题的回答情况，你会得到一些后续提问，比如*为什么泛型是由类型擦除来实现的*或者给你展示一些会导致编译器出错的错误泛型代码。请阅读我的[Java中泛型是如何工作的](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fjavarevisited.blogspot.com%2F2011%2F09%2Fgenerics-java-example-tutorial.html)来了解更多信息。

 

**3. 什么是泛型中的限定通配符和非限定通配符 ?**

这是另一个非常[流行的Java泛型面试题](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fjavarevisited.blogspot.com%2F2011%2F04%2Ftop-20-core-java-interview-questions.html)。限定通配符对类型进行了限制。有两种限定通配符，一种是<? extends T>它通过确保类型必须是T的子类来设定类型的上界，另一种是<? super T>它通过确保类型必须是T的父类来设定类型的下界。泛型类型必须用限定内的类型来进行初始化，否则会导致编译错误。另一方面<?>表示了非限定通配符，因为<?>可以用任意类型来替代。更多信息请参阅我的文章[泛型中限定通配符和非限定通配符之间的区别](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fjavarevisited.blogspot.com%2F2012%2F04%2Fwhat-is-bounded-and-unbounded-wildcards.html)。

 

**4. List<? extends T>和List <? super T>之间有什么区别 ?**

这和上一个面试题有联系，有时面试官会用这个问题来评估你对泛型的理解，而不是直接问你什么是限定通配符和非限定通配符。这两个List的声明都是[限定通配符的例子](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fjavarevisited.blogspot.sg%2F2012%2F04%2Fwhat-is-bounded-and-unbounded-wildcards.html)，List<? extends T>可以接受任何继承自T的类型的List，而List<? super T>可以接受任何T的父类构成的List。例如List<? extends Number>可以接受List<Integer>或List<Float>。在本段出现的连接中可以找到更多信息。

 

**5. 如何编写一个泛型方法，让它能接受泛型参数并返回泛型类型?**

编写泛型方法并不困难，你需要用泛型类型来替代原始类型，比如使用T, E or K,V等被广泛认可的类型占位符。泛型方法的例子请参阅[Java集合类框架](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fjavarevisited.blogspot.sg%2F2011%2F11%2Fcollection-interview-questions-answers.html)。最简单的情况下，一个泛型方法可能会像这样:

```
public V put(K key, V value) {
        return cache.put(key, value);
} 
```

 

**6. Java中如何使用泛型编写带有参数的类?**

这是上一道面试题的延伸。面试官可能会要求你*用泛型编写一个类型安全的类*，而不是编写一个泛型方法。关键仍然是使用泛型类型来代替原始类型，而且要使用JDK中采用的标准占位符。

**7. 编写一段泛型程序来实现LRU缓存?**

对于喜欢[Java编程](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fjavarevisited.blogspot.sg%2F2011%2F09%2Fcode-review-checklist-best-practice.html)的人来说这相当于是一次练习。给你个提示，LinkedHashMap可以用来实现固定大小的LRU缓存，当LRU缓存已经满了的时候，它会把最老的键值对移出缓存。LinkedHashMap提供了一个称为removeEldestEntry()的方法，该方法会被put()和putAll()调用来删除最老的键值对。当然，如果你已经编写了一个可运行的[JUnit测试](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fjavarevisited.blogspot.sg%2F2012%2F06%2Fjunit4-annotations-test-examples-and.html)，你也可以随意编写你自己的实现代码。

 

**8. 你可以把****List<String>传递给一个接受****List<Object>参数的方法吗？**

对任何一个不太熟悉泛型的人来说，这个Java泛型题目看起来令人疑惑，因为乍看起来String是一种Object，所以List<String>应当可以用在需要List<Object>的地方，但是事实并非如此。真这样做的话会导致编译错误。如果你再深一步考虑，你会发现Java这样做是有意义的，因为List<Object>可以存储任何类型的对象包括[String, Integer](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fjavarevisited.blogspot.com%2F2011%2F08%2Fconvert-string-to-integer-to-string.html)等等，而List<String>却只能用来存储Strings。

```
List<Object> objectList;
List<String> stringList;
     
objectList = stringList;  //compilation error incompatible types
```

 

**9. Array中可以用泛型吗?**

这可能是Java泛型面试题中最简单的一个了，当然前提是你要知道Array事实上并不支持泛型，这也是为什么Joshua Bloch在[Effective Java](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fwww.amazon.com%2Fdp%2F0321356683%2F%3Ftag%3Djavamysqlanta-20)一书中建议使用List来代替Array，因为*List可以提供编译期的类型安全保证*，而Array却不能。

**10. 如何阻止Java中的类型未检查的警告?**

如果你把泛型和原始类型混合起来使用，例如下列代码，Java 5的javac编译器会产生类型未检查的警告，例如

```
List<String> rawList = new ArrayList()
注意: Hello.java使用了未检查或称为不安全的操作; 
```

这种警告可以使用@SuppressWarnings("unchecked")注解来屏蔽。

 

***\*Java\**中****List<Object>和原始类型****List之间的区别?**

原始类型和带参数类型<Object>之间的主要区别是，在编译时[编译器](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fjavarevisited.blogspot.sg%2F2011%2F12%2Fjre-jvm-jdk-jit-in-java-programming.html)不会对原始类型进行类型安全检查，却会对带参数的类型进行检查，通过使用Object作为类型，可以告知编译器该方法可以接受任何类型的对象，比如String或Integer。这道题的考察点在于对泛型中原始类型的正确理解。它们之间的第二点区别是，你可以把任何带参数的类型传递给原始类型List，但却不能把List<String>传递给接受List<Object>的方法，因为会产生编译错误。更多详细信息请参阅[Java中的泛型是如何工作的](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fjavarevisited.blogspot.sg%2F2011%2F09%2Fgenerics-java-example-tutorial.html)。

**Java中List<?>和****List<Object>之间的区别是什么****?**

这道题跟上一道题看起来很像，实质上却完全不同。*List<?>* *是一个未知类型的List，*而*List<Object>其实是任意类型的**List*。你可以把List<String>, List<Integer>赋值给List<?>，却不能把List<String>赋值给List<Object>。   

```
List<?> listOfAnyType;
List<Object> listOfObject = new ArrayList<Object>();
List<String> listOfString = new ArrayList<String>();
List<Integer> listOfInteger = new ArrayList<Integer>();
     
listOfAnyType = listOfString; //legal
listOfAnyType = listOfInteger; //legal
listOfObjectType = (List<Object>) listOfString; //compiler error - in-convertible types 
```

**List<String>和原始类型List之间的区别.**

该题类似于“原始类型和带参数类型之间有什么区别”。带参数类型是类型安全的，而且其类型安全是由编译器保证的，但[原始类型List却不是类型安全的](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Fjavarevisited.blogspot.sg%2F2012%2F04%2Fdifference-between-list-and-set-in-java.html)。你不能把String之外的任何其它类型的Object存入String类型的List中，而你可以把任何类型的对象存入原始List中。使用泛型的带参数类型你不需要进行类型转换，但是对于原始类型，你则需要进行显式的类型转换。

```
List listOfRawTypes = new ArrayList();
listOfRawTypes.add("abc");
listOfRawTypes.add(123); //编译器允许这样 - 运行时却会出现异常
String item = (String) listOfRawTypes.get(0); //需要显式的类型转换
item = (String) listOfRawTypes.get(1); //抛ClassCastException，因为Integer不能被转换为String
     
List<String> listOfString = new ArrayList();
listOfString.add("abcd");
listOfString.add(1234); //编译错误，比在运行时抛异常要好
item = listOfString.get(0); //不需要显式的类型转换 - 编译器自动转换 
```



## 线程和进程的区别

1、地址空间：每个进程都有自己的虚拟地址空间，进程内的所有线程共享进程的虚拟地址空间。

2、资源拥有：同一进程内的线程共享本进程的资源，但是进程之间的资源是独立的。

3、一个进程崩溃后，在保护模式下不会对其他进程产生影响，但是一个线程崩溃整个进程都死掉。所以多进程要比多线程健壮。

4、进程切换时，消耗的资源大，效率高。所以涉及到频繁的切换时，使用线程要好于进程。同样如果要求同时进行并且又要共享某些变量的并发操作，只能用线程不能用进程。

进程切换虚拟地址空间，切换内核栈和硬件上下文。线程只需要切换内核栈和硬件上下文。

5、执行过程：每个独立的进程程有一个程序运行的入口、顺序执行序列和程序入口。但是线程不能独立执行，必须依存在应用程序中，由应用程序提供多个线程执行控制。

6、线程是处理器调度和分配的基本单位，进程作为拥有资源的基本单位。

7、两者均可并发执行。

优缺点：

线程执行开销小，但是不利于资源的管理和保护。线程适合在SMP机器（双CPU系统）上运行。

进程执行开销大，但是能够很好的进行资源管理和保护。进程可以跨机器前移。

## 线程状态

![img](https://img2020.cnblogs.com/blog/1842338/202110/1842338-20211011115638685-1098558362.jpg)



## synchronized

[深入理解synchronized底层原理，一篇文章就够了！ - 云+社区 - 腾讯云 (tencent.com)](https://cloud.tencent.com/developer/article/1465413)

[深入分析Synchronized原理(阿里面试题) - aspirant - 博客园 (cnblogs.com)](https://www.cnblogs.com/aspirant/p/11470858.html)

synchronized会锁住类或是该类的某一个实例对象，这取决于他的作用域。

锁类

- 对类的静态方法加锁
- 在同步块中对类加锁

锁对象

- 对该对象的成员方法加锁
- 在同步块中对对象加锁



**同步方法**

方法级的同步是隐式，即无需通过字节码指令来控制的，它实现在方法调用和返回操作之中。**JVM可以从方法常量池中的方法表结构(method_info Structure) 中的 ACC_SYNCHRONIZED 访问标志区分一个方法是否同步方法**。

当方法调用时，调用指令将会 检查方法的 ACC_SYNCHRONIZED 访问标志是否被设置，如果设置了，执行线程将先持有monitor（虚拟机规范中用的是管程一词）， 然后再执行方法，最后再方法完成(无论是正常完成还是非正常完成)时释放monitor。

在方法执行期间，执行线程持有了monitor，其他任何线程都无法再获得同一个monitor。

如果一个同步方法执行期间抛 出了异常，并且在方法内部无法处理此异常，那这个同步方法所持有的monitor将在异常抛到同步方法之外时自动释放。



**同步代码块**

**同步块是由monitorenter指令进入，然后monitorexit释放锁**，在执行monitorenter之前需要尝试获取锁，如果这个对象没有被锁定，或者当前线程已经拥有了这个对象的锁，那么就把锁的计数器加1。当执行monitorexit指令时，锁的计数器也会减1。当获取锁失败时会被阻塞，一直等待锁被释放。

值得注意的是编译器将会确保无论方法通过何种方式完成，方法中调用过的每条 monitorenter 指令都有执行其对应 monitorexit 指令，而无论这个方法是正常结束还是异常结束。

为了保证在方法异常完成时 monitorenter 和 monitorexit 指令依然可以正确配对执行，编译器会自动产生一个异常处理器，这个异常处理器声明可处理所有的异常，它的目的就是用来执行 monitorexit 指令。从字节码中也可以看出多了一个monitorexit指令，它就是异常结束时被执行的释放monitor 的指令。



**底层实现**

[Java-Notes/对象的内存布局.md at master · leosanqing/Java-Notes (github.com)](https://github.com/leosanqing/Java-Notes/blob/master/JVM/对象的内存布局/对象的内存布局.md)

在理解锁实现原理之前先了解一下 Java 的对象头和 Monitor ，在 JVM 中，对象是分成三部分存在的：对象头、实例数据、对齐填充。

![fu98yi2bmj](../img/fu98yi2bmj.jpg)

实例数据和对齐填充与 synchronized 无关。**实例数据**存放类的属性数据信息，包括父类的属性信息，如果是数组的实例部分还包括数组的长度，这部分内存按4字节对齐；**对其填充**不是必须部分，由于虚拟机要求对象起始地址必须是8字节的整数倍，对齐填充仅仅是为了使字节对齐。

对象头是我们需要关注的重点，它是synchronized实现锁的基础，因为synchronized申请锁、上锁、释放锁都与对象头有关。对象头主要结构是由 `Mark Word` 和 `Class Metadata Address` 组成，**其中** `Mark Word` **存储对象的 hashCode、锁信息或分代年龄或GC标志等信息**，`Class Metadata Address` **是类型指针指向对象的类元数据，JVM 通过该指针确定该对象是哪个类的实例**。

锁也分不同状态，在 JDK6 之后有四个状态：**无锁状态、偏向锁、轻量级锁、重量级锁**，其中无锁就是一种状态了。锁的类型和状态在对象头`Mark Word`中都有记录，在申请锁、锁升级等过程中JVM都需要读取对象的`Mark Word`数据。

每一个锁都对应一个monitor对象，在HotSpot虚拟机中它是由ObjectMonitor实现的（C++实现）。每个对象都存在着一个monitor与之关联，对象与其monitor之间的关系有存在多种实现方式，如monitor可以与对象一起创建销毁或当线程试图获取对象锁时自动生成，但当一个monitor被某个线程持有后，它便处于锁定状态。



**锁膨胀**

锁有四种状态，并且会因实际情况进行膨胀升级，其膨胀方向是：**无锁——>偏向锁——>轻量级锁——>重量级锁**，并且膨胀方向不可逆。



[Java-Notes/锁对比.md at master · leosanqing/Java-Notes (github.com)](https://github.com/leosanqing/Java-Notes/blob/master/ConcurrencyProgramming/0-基础/锁对比/锁对比.md)

### 偏向锁

一句话总结它的作用：**减少统一线程获取锁的代价**。在大多数情况下，锁不存在多线程竞争，总是由同一线程多次获得，那么此时就是偏向锁。



**核心思想：**

如果一个线程获得了锁，那么锁就进入偏向模式，此时`Mark Word`的结构也就变为偏向锁结构，**当该线程再次请求锁时，无需再做任何同步操作，即获取锁的过程只需要检查**`Mark Word`**的锁标记位为偏向锁以及当前线程ID等于**`Mark Word`**的ThreadID即可**，这样就省去了大量有关锁申请的操作。



**初始化过程**

- 当锁对象**第一次**被线程获取的时候，虚拟机会将对象头中的锁标志位置为 "01"(偏向模式)
- 同时，使用CAS(如果不了解CAS，可以看这篇文章，[悲观锁和乐观锁](https://github.com/leosanqing/Java-Notes/blob/master/ConcurrencyProgramming/0-基础/悲观锁和乐观锁/悲观锁和乐观锁.md))操作，把获取到这个锁的**线程的ID**记录在对象的MW中，
- **如果 CAS成功，持有偏向锁的线程每次进入这个锁相关的同步块时，虚拟机可以不进行任何同步操作**



**撤销过程**

- 首先暂停拥有偏向锁的线程
- 然后检查持有偏向锁的线程是否活着
  - 不活跃，将对象头设置成无锁状态 (标志位"01"，但不可偏向)
  - 活跃，
    - CAS成功，重新偏向，更改线程ID
    - 失败，恢复成无锁状态，或者变成轻量级锁定状态。





### 轻量级锁

轻量级锁是由偏向锁升级而来，当存在第二个线程申请同一个锁对象时，偏向锁就会立即升级为轻量级锁。

他的出现并不是代替重量级锁，**而是在没有多线程竞争的前提下，减少系统互斥量操作产生的性能消耗**



**加锁**

- 线程在执行同步块之前，JVM会现在当前线程的**栈帧**中创建用于存储**锁记录**（下图的Lock Record）的空间，并将对象头中的MW复制到**锁记录**中，官方称为 Displaced Mark Word
- 然后，虚拟机将使用CAS操作，将对象的MW更新为指向**锁记录**的指针
  - 如果这个操作成功，那么该线程就有了该对象的锁，并且对象的MW的锁标志位置为 "00"，表示该对象处于轻量级锁定状态
  - 如果更新失败，表示其他线程竞争锁，当前线程尝试使用**自旋**来获取锁



**解锁**

- 使用CAS操作将 Displaced Mark Word 替换回到对象头
  - 如果成功，则说明没有发生竞争
  - 失败，则表示当前锁存在竞争，锁就会膨胀成重量级锁
    - 释放锁，并且唤醒等待的线程



**缺点**

轻量级能提升程序同步性能的依据是"对于绝大部分的锁，**在整个同步周期内都是不存在竞争的**"，这是一个经验数据。

- 如果没有竞争，轻量级锁使用CAS操作，避免使用互斥量
- 如果存在竞争，除了互斥量的开销，还有 CAS的操作，不仅没有提升，反而性能会下降



### 重量级锁

[Java Synchronized 重量级锁原理深入剖析上(互斥篇)_小鱼人爱编程的博客-CSDN博客_java重量级锁原理](https://blog.csdn.net/wekajava/article/details/120306478)

重量级锁引入 ObjectMonitor 类，可在线程间共享，方便其他线程找到被阻塞的该线程。

通过修改 Mark Word 来指向该对象。



**加锁**

- 多次尝试加锁，其中会使用自旋。
- 如果加锁失败，将线程包装，加入阻塞队列。
- 再次尝试，如果失败，将自己挂起。
- 被唤醒后继续尝试获取锁



**解锁**

- 先释放锁
- 如果有线程等待被唤醒，尝试唤醒线程，这过程中可能被其他线程抢占



### 对比

|    锁    |                             优点                             |                      缺点                      |             适用场景              |
| :------: | :----------------------------------------------------------: | :--------------------------------------------: | :-------------------------------: |
|  偏向锁  | 加锁和解锁都不需要额外的消耗，和执行非同步方法相比仅存在纳秒级的差距 | 如果线程间存在锁竞争，会带来额外的锁撤销的消耗 |      只有一个线程访问同步块       |
| 轻量级锁 |           竞争的线程不会阻塞，提高了程序的响应速度           | 如果始终得不到锁竞争的线程，使用自旋会消耗CPU  | 追求响应时间 同步块执行速度非常块 |
| 重量级锁 |               线程竞争不使用自旋，不会消耗CPU                |              线程阻塞，响应时间慢              |   追求吞吐量 同步块执行时间较长   |



**锁消除**

消除锁是虚拟机另外一种锁的优化，这种优化更彻底，在 JIT 编译时，对运行上下文进行扫描，去除不可能存在竞争的锁。



**锁粗化**

锁粗化是虚拟机对另一种极端情况的优化处理，通过扩大锁的范围，避免反复加锁和释放锁。



## CAS

CAS是compare and swap的缩写，即我们所说的比较交换。cas是一种基于锁的操作，而且是乐观锁。

乐观锁总是假设最好的情况，每次去拿数据的时候都认为别人不会修改，所以不会上锁，但是在更新的时候会判断一下在此期间别人有没有去更新这个数据，可以使用版本号机制和CAS算法实现。乐观锁适用于多读的应用类型，这样可以提高吞吐量。

CAS 操作包含三个操作数 —— 内存位置（V）、预期原值（A）和新值(B)。如果内存地址里面的值和A的值是一样的，那么就将内存里面的值更新成B。CAS是通过自旋来获取数据的，若果在第一轮循环中，a线程获取地址里面的值被b线程修改了，那么a线程需要自旋，到下次循环才有可能机会执行。



## volatile



1. 保证了不同线程对这个变量进行操作时的可见性，当一个共享变量被volatile修饰时，它会保证修改的值会立即被更新到主存，当有其他线程需要读取时，它会去内存中读取新值。
2. 禁止进行指令重排序。禁止语句越过 volatile 修饰的变量重排。

**指令重排**

为了提高执行效率，CPU会将没有依赖关系的指令重新排序。如果希望控制重新排序，可以使用volatile修饰一个变量，包含该变量的指令前后的指令各自独立排序，前后指令不能交叉排序。



volatile 只能保证一个线程从堆中获取数据时获取的是当前所有线程中的最新值，假如一个线程已经从堆中复制了数据，在操作完成前，其他线程修改了数据，修改后的数据并不会同步到当前线程中。

这时需要 CAS。

**原理**

“观察加入volatile关键字和没有加入volatile关键字时所生成的汇编代码发现，加入volatile关键字时，会多出一个lock前缀指令”

lock前缀指令实际上相当于一个内存屏障（也成内存栅栏），内存屏障会提供3个功能：

1）它确保指令重排序时不会把其后面的指令排到内存屏障之前的位置，也不会把前面的指令排到内存屏障的后面；即在执行到内存屏障这句指令时，在它前面的操作已经全部完成；

2）它会强制将对缓存的修改操作立即写入主存；

3）如果是写操作，它会导致其他CPU中对应的缓存行无效。





## 死锁

死锁是指两个或两个以上的线程在执行过程中，因争夺资源而造成的一种互相等待的现象，若无外力作用，它们都将无法推进下去。

例如，某计算机系统中只有一台打印机和一台输入 设备，进程P1正占用输入设备，同时又提出使用打印机的请求，但此时打印机正被进程P2 所占用，而P2在未释放打印机之前，又提出请求使用正被P1占用着的输入设备。这样两个进程相互无休止地等待下去，均无法继续执行，此时两个进程陷入死锁状态。



### 如何避免死锁

- 加锁顺序（线程按照一定的顺序加锁）
  - 当多个线程需要相同的一些锁，但是按照不同的顺序加锁，死锁就很容易发生。如果能确保所有的线程都是按照相同的顺序获得锁，那么死锁就不会发生。
  - 避免嵌套锁：这是死锁最常见的原因，如果您已经持有一个资源，请避免锁定另一个资源。
- 加锁时限（线程尝试获取锁的时候加上一定的时限，超过时限则放弃对该锁的请求，并释放自己占有的锁）
  - 避免无限期等待：在尝试获取锁的时候加一个超时时间，这也就意味着在尝试获取锁的过程中若超过了这个时限该线程则放弃对该锁请求。
- 死锁检测
  - 死锁检测是一个更好的死锁预防机制，它主要是针对那些不可能实现按序加锁并且锁超时也不可行的场景。
  - 一个可行的做法是释放所有锁，回退，并且等待一段随机的时间后重试。这个和简单的加锁超时类似，不一样的是只有死锁已经发生了才回退，而不会是因为加锁的请求超时了。虽然有回退和等待，但是如果有大量的线程竞争同一批锁，它们还是会重复地死锁（*原因同超时类似，不能从根本上减轻竞争*）。
  - 一个更好的方案是给这些线程设置优先级，让一个（或几个）线程回退，剩下的线程就像没发生死锁一样继续保持着它们需要的锁。如果赋予这些线程的优先级是固定不变的，同一批线程总是会拥有更高的优先级。为避免这个问题，可以在死锁发生的时候设置随机的优先级。



**只锁需要的部分**

只获对需要的资源加锁，如果我们只需要对象的一个字段，那么我们应该只锁定那个特定的字段而不是完整的对象。

**避免无限期等待**

如果两个线程使用 thread join 无限期互相等待也会造成死锁，我们可以设定等待的最大时间来避免这种情况。



### 死锁案例

```java
public class DeadLock {
    public static String obj1 = "obj1";
    public static String obj2 = "obj2";

    public static void main(String[] args) {
        Thread a = new Thread(new Lock1());
        Thread b = new Thread(new Lock2());
        a.start();
        b.start();
    }
}

class Lock1 implements Runnable {
    @Override
    public void run() {
        try {
            System.out.println("Lock1 running");
            while (true) {
                synchronized (DeadLock.obj1) {
                    System.out.println("Lock1 lock obj1");
                    //获取obj1后先等一会儿，让Lock2有足够的时间锁住obj2
                    Thread.sleep(3000);
                    synchronized (DeadLock.obj2) {
                        System.out.println("Lock1 lock obj2");
                    }
                }
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

class Lock2 implements Runnable {
    @Override
    public void run() {
        try {
            System.out.println("Lock2 running");
            while (true) {
                synchronized (DeadLock.obj2) {
                    System.out.println("Lock2 lock obj2");
                    Thread.sleep(3000);
                    synchronized (DeadLock.obj1) {
                        System.out.println("Lock2 lock obj1");
                    }
                }
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```









## JVM

[jvm内存模型-和内存分配以及jdk、jre、jvm是什么关系(阿里，美团，京东) - aspirant - 博客园 (cnblogs.com)](https://www.cnblogs.com/aspirant/p/6841955.html)

**1.什么是jvm?**

（1）jvm是一种用于计算设备的规范，它是一个虚构出来的机器，是通过在实际的计算机上仿真模拟各种功能实现的。

（2）jvm包含一套字节码指令集，一组寄存器，一个栈，一个垃圾回收堆和一个存储方法域。

（3）JVM屏蔽了与具体操作系统平台相关的信息，使Java程序只需生成在Java虚拟机上运行的目标代码（字节码）,就可以在多种平台上不加修改地运行。

JVM在执行字节码时，实际上最终还是把字节码解释成具体平台上的机器指令执行。

**2.jdk、jre、jvm是什么关系？**

（1）JRE(Java Runtime Environment)，也就是java平台。所有的java程序都要在JRE环境下才能运行。

（2）JDK(Java Development Kit)，是开发者用来编译、调试程序用的开发包。JDK也是JAVA程序需要在JRE上运行。

（3）JVM(Java Virtual Machine)，是JRE的一部分。它是一个虚构出来的计算机，是通过在实际的计算机上仿真模拟各种计算机功能来实现的。

JVM有自己完善的硬件架构，如处理器、堆栈、寄存器等，还具有相应的指令系统。

Java语言最重要的特点就是跨平台运行。使用JVM就是为了支持与操作系统无关，实现跨平台。

**3.JVM原理**

（1）jvm是java的核心和基础，在java编译器和os平台之间的虚拟处理器，可在上面执行字节码程序。

（2）java编译器只要面向jvm，生成jvm能理解的字节码文件。java源文件经编译成字节码程序，通过jvm将每条指令翻译成不同的机器码，通过特定平台运行。(JIT即时编译器Just-In-Time Compiler)



![img](https://images2015.cnblogs.com/blog/539365/201511/539365-20151119102212311-886733816.png)

**4. JVM执行程序的过程**

1) 加载.class文件  具体参考：[Java 类加载机制(阿里面试题)](http://www.cnblogs.com/aspirant/p/7200523.html)
2) 管理并分配内存 
3) 执行垃圾收集
   JRE（java运行时环境）由JVM构造的java程序的运行环，也是Java程序运行的环境，但是他同时一个操作系统的一个应用程序一个进程，
   因此他也有他自己的运行的生命周期，也有自己的代码和数据空间。
   JVM在整个jdk中处于最底层，负责于操作系统的交互，用来屏蔽操作系统环境，
   提供一个完整的Java运行环境，因此也就虚拟计算机。

1) 创建JVM装载环境和配置 
2) 装载JVM.dll 
3) 初始化JVM.dll并挂界到JNIENV(JNI调用接口)实例
4) 调用JNIEnv实例装载并处理class类。

**5. JVM的生命周期**
JVM实例对应了一个独立运行的java程序它是进程级别

a) 启动。启动一个Java程序时，一个JVM实例就产生了，任何一个拥有public static void main(String[] args)函数的class都可以作为JVM实例运行的起点 

b) 运行。main()作为该程序初始线程的起点，任何其他线程均由该线程启动。JVM内部有两种线程：守护线程和非守护线程，main()属于非守护线程，守护线程通常由JVM自己使用，java程序也可以表明自己创建的线程是守护线程 

c) 消亡。当程序中的所有非守护线程都终止时，JVM才退出；若安全管理器允许，程序也可以使用Runtime类或者System.exit()来退出

JVM执行引擎实例则对应了属于用户运行程序的线程它是线程级别的

**6、JVM内存模型**

（1）java代码具体执行过程如下图，

![img](https://images2015.cnblogs.com/blog/539365/201511/539365-20151119103542765-547992652.png)

（2）运行时数据区，即jvm内存结构图如下图

![img](https://images2015.cnblogs.com/blog/539365/201511/539365-20151119103724608-1752144990.png)

（3）运行时数据区存储了哪些数据？

　　a) 程序计数器(PC寄存器)

　　　  由于在JVM中，多线程是通过线程轮流切换来获得CPU执行时间的，因此，在任一具体时刻，一个CPU的内核只会执行一条线程中的指令，

　　因此，为了能够使得每个线程都在线程切换后能够恢复在切换之前的程序执行位置，每个线程都需要有自己独立的程序计数器，并且不能互相被干扰，

　　否则就会影响到程序的正常执行次序。因此，可以这么说，程序计数器是每个线程所私有的。由于程序计数器中存储的数据所占空间的大小不会随程序的执行而发生改变，

　　因此，对于程序计数器是不会发生内存溢出现象(OutOfMemory)的。

　　b) java栈

　　　  Java栈中存放的是一个个的栈帧，每个栈帧对应一个被调用的方法，在栈帧中包括**局部变量表(Local Variables)**、**操作数栈(Operand Stack)**、

　　　　指向当前方法所属的类的运行时常量池（运行时常量池的概念在方法区部分会谈到）**的引用**(Reference to runtime constant pool)、

　　　　**方法返回地址(Return Address)**和一些额外的附加信息。当线程执行一个方法时，就会随之创建一个对应的栈帧，并将建立的栈帧压栈。当方法执行完毕之后，便会将栈帧出栈。　

![img](https://images2015.cnblogs.com/blog/539365/201511/539365-20151119105009030-922518460.png)

　　c）本地方法栈

　　本地方法栈与Java栈的作用和原理非常相似。区别只不过是Java栈是为执行Java方法服务的，而本地方法栈则是为执行本地方法（Native Method）服务的

　　d）堆

　　Java中的堆是用来存储对象本身的以及数组（数组引用是存放在Java栈中的）。**堆是被所有线程共享的，在JVM中只有一个堆。**

　　e）方法区

　　与堆一样，是被线程共享的区域。在方法区中，存储了每个类的信息（包括类的名称、方法信息、字段信息）、静态变量、常量以及编译器编译后的代码等。

　　在Class文件中除了类的字段、方法、接口等描述信息外，还有一项信息是常量池，用来存储编译期间生成的字面量和符号引用。

　　在方法区中有一个非常重要的部分就是运行时常量池，它是每一个类或接口的常量池的运行时表示形式，在类和接口被加载到JVM后，

　　对应的运行时常量池就被创建出来。当然并非Class文件常量池中的内容才能进入运行时常量池，在运行期间也可将新的常量放入运行时常量池中，比如String的intern方法。

　　**7、JVM内存溢出的情况**

　　![img](https://images2015.cnblogs.com/blog/539365/201511/539365-20151119105947202-10960285.png)

　　a) 程序计数器（Program Counter Register）

　　每条线程都有一个独立的的程序计数器，各线程间的计数器互不影响，因此该区域是线程私有的。该内存区域是唯一一个在Java虚拟机规范中没有规定任何OOM（内存溢出：OutOfMemoryError）情况的区域。只存下一个字节码指令的地址，消耗内存小且固定，无论方法多深，他只存一条。

　　b)Java虚拟机栈（Java Virtual Machine Stacks）

　　　　在Java虚拟机规范中，对这个区域规定了两种异常情况：

  　 1、如果线程请求的栈深度大于虚拟机所允许的深度，将抛出StackOverflowError异常。

  　　2、如果虚拟机在动态扩展栈时无法申请到足够的内存空间，则抛出OutOfMemoryError异常。

  　　   这两种情况存在着一些互相重叠的地方：当栈空间无法继续分配时，到底是内存太小，还是已使用的栈空间太大，其本质上只是对同一件事情的两种描述而已。

　　　　  在单线程的操作中，无论是由于栈帧太大，还是虚拟机栈空间太小，当栈空间无法分配时，虚拟机抛出的都是StackOverflowError异常，而不会得到OutOfMemoryError异常。

　     　而在多线程环境下，则会抛出OutOfMemoryError异常。

　　c)堆Java Heap

　　　　Java Heap是Java虚拟机所管理的内存中最大的一块，它是所有线程共享的一块内存区域。几乎所有的对象实例和数组都在这里分配内存。Java Heap是垃圾收集器管理的主要区域，因此很多时候也被称为“GC堆”。

  　　根据Java虚拟机规范的规定，Java堆可以处在物理上不连续的内存空间中，只要逻辑上是连续的即可。如果在堆中没有内存可分配时，并且堆也无法扩展时，将会抛出OutOfMemoryError异常。  

　　d)方法区域，又被称为“永久代”，当方法区无法满足内存分配需求时，将抛出OutOfMemoryError异常。 

关于垃圾回收算法
(1)目前根据 Mark-Sweep算法 延伸出来了CMS算法（concurrent Mark-Sweep）算法

(2) G1(Garbage First)算法

这两个阿里的面试官问过他们的区别：

我做了整理：

参考：[JVM的垃圾回收机制 总结(垃圾收集、回收算法、垃圾回收器)](http://www.cnblogs.com/aspirant/p/8662690.html)

参考：[图解 CMS 垃圾回收机制原理，-阿里面试题](http://www.cnblogs.com/aspirant/p/8663911.html)

参考：[G1 垃圾收集器入门](http://www.cnblogs.com/aspirant/p/8663872.html) 

参考：[CMS收集器和G1收集器优缺点](http://www.cnblogs.com/aspirant/p/8663897.html) 

参考：[jvm内存模型和内存分配](http://www.cnblogs.com/fubaizhaizhuren/p/4976839.html)

参考：[jvm-java 内存模型 以及各个分区具体内容](https://blog.csdn.net/steady_pace/article/details/51254740)





## 内存区域





<img src="https://pics7.baidu.com/feed/9345d688d43f87949c14c60c544b59fd1ad53a86.png?token=cbd79daaae963950c1c907c532aa1d09" alt="img"  />





| 数据区     |                                                              |
| ---------- | ------------------------------------------------------------ |
| Java 堆    | 存放对象实例                                                 |
| 方法区     | 类信息、常量、静态变量、即时编译后的代码                     |
| 本地方法栈 | 为虚拟机使用到的Native方法服务                               |
| 程序计数器 | 可以看作是当前线程执行的字节码的行号指令器，为了线程正确切换而服务 |
| 虚拟机栈   | 局部变量表、操作数栈、动态链接、方法出口                     |



- 线程私有
  - 虚拟机栈
  - 本地方法栈（不是所有JVM都有，比如Hotspot）
  - 程序计数器
- 线程共享
  - 方法区
  - 堆





### 线程私有



**虚拟机栈**

java虚拟机栈是**线程私有的**，他的生命周期和线程相同。**他描述的是Java方法执行的内存模型：每个方法在执行的同时都会创建一个栈帧用于存储局部变量表、操作数栈、动态链接、方法出口等信息。每个方法从调用直到执行完的过程，就对应这一个栈帧在虚拟机栈中入栈到出栈的过程**。

**栈帧**

他存放了以下重要信息（部分）：

- 局部变量表
- 操作数栈
- 动态链接
- 方法出口
- 等……..

**slot**

我们刚刚说到栈帧的数据结构，他存储的重要信息，其中有一个是**局部变量表**，而这个局部变量表也是由一个个小的数据结构组成，他就叫**局部变量空间（slot）**。你也可以把它当成是一个空间大小的度量单位，就像字节一样，因为存储的数据的大小也是用这个衡量的。

局部变量表存放了编译期可知的各种**基本数据类型**(boolean、byte、char、short、int、float、long、double)、**对象引用**(reference类型)和**returnAddress类型**。



**本地方法栈**

[JVM的本地方法栈 - wade&luffy - 博客园 (cnblogs.com)](https://www.cnblogs.com/wade-luffy/p/5813747.html)

**注意：有的虚拟机中是将本地方法栈和虚拟机栈合在一起的，比如Hotspot虚拟机**

本地方法栈和虚拟机栈差不多，不过 Java虚拟机栈为虚拟机执行Java方法服务，而本地方法栈为虚拟机使用到的Native方法服务。我们知道Java虚拟机有一部分是用其他语言编写的，比如C/C++,因此他有一部分是这些语言的类库方法。

**Navtive 方法是 Java 通过 JNI 直接调用本地 C/C++ 库**，可以认为是 Native 方法相当于 C/C++ 暴露给 Java 的一个接口，Java 通过调用这个接口从而调用到 C/C++ 方法。当线程调用 Java 方法时，虚拟机会创建一个栈帧并压入 Java 虚拟机栈。然而当它调用的是 native 方法时，虚拟机会保持 Java 虚拟机栈不变，也不会向 Java 虚拟机栈中压入新的栈帧，虚拟机只是简单地动态连接并直接调用指定的 native 方法。



**程序计数器**

程序计数器是线程私有的，他是一块较小的内存空间，他可以看作是当前线程执行的字节码的行号指令器。在虚拟机的概念模型里(仅仅是概念模型，不同虚拟机的实现方式可能有更高效的方法)，字节码解释器工作时就是通过改变这个计数器的值来选取下一条需要执行的字节码指令，分支、循环、跳转、异常处理等基础功能都需要依赖这个计数器。

**为什么线程私有**

Java虚拟机的多线程是通过线程轮流切换并分配处理器执行时间的方式来实现的，在任何一个确定的时刻，一个处理器(对于多核处理器来说是一个内核)都只会执行一条线程中的指令、因此**为了线程切换后能恢复到正确的执行位置，每条线程都需要有一个独立的程序计数器，各条线程之间计数器互不影响，独立存储**，我们称这类内存区域为"线程私有"的内存。



### 线程共享

这里是GC垃圾回收重点"照顾"的对象，可以参考：[JVM垃圾回收](https://github.com/leosanqing/Java-Notes/blob/master/JVM/JVM垃圾回收.md)



**Java堆**

对于大所数应用来说，Java堆是Java虚拟机所管理的内存中最大的一块，也被线程共享。**唯一的目的就是存放对象实例，几乎所有的对象实例都在这里分配内存**

他还可以再细分为：新生代，老年代



**方法区**

和Java堆一样是线程共享的，它用于存储已经被虚拟机加载的：

- 类信息
- 常量
- 静态变量
- 即时编译后的代码
- 等…...



### OOM

java.lang.OutOfMemoryError: Java heap space ------>java堆内存溢出，此种情况最常见，一般由于内存泄露或者堆的大小设置不当引起。对于内存泄露，需要通过内存监控软件查找程序中的泄露代码，而堆大小可以通过虚拟机参数-Xms,-Xmx等修改。

java.lang.OutOfMemoryError: PermGen space ------>java永久代溢出，即方法区溢出了，一般出现于大量Class或者jsp页面，或者采用cglib等反射机制的情况，因为上述情况会产生大量的Class信息存储于方法区。此种情况可以通过更改方法区的大小来解决，使用类似-XX:PermSize=64m -XX:MaxPermSize=256m的形式修改。另外，过多的常量尤其是字符串也会导致方法区溢出。

java.lang.StackOverflowError ------> 不会抛OOM error，但也是比较常见的Java内存溢出。JAVA虚拟机栈溢出，一般是由于程序中存在死循环或者深度递归调用造成的，栈大小设置太小也会出现此种溢出。可以通过虚拟机参数-Xss来设置栈的大小。





## 类加载

[Java 类加载机制(阿里)-何时初始化类 - aspirant - 博客园 (cnblogs.com)](https://www.cnblogs.com/aspirant/p/7200523.html)

[java中类加载时机 - aspirant - 博客园 (cnblogs.com)](https://www.cnblogs.com/aspirant/p/9036010.html)



类加载器是负责读取 Java 字节代码，并转换成 `java.lang.Class` 类的一个实例。

### 相同判断

类加载器除了用于加载类外，还可用于确定类在 Java 虚拟机中的唯一性。

即便是同样的字节代码，被不同的类加载器加载之后所得到的类，也是不同的。

通俗一点来讲，要判断两个类是否“相同”，前提是这两个类必须被同一个类加载器加载，否则这个两个类不“相同”。
这里指的“相同”，包括类的Class对象的`equals()`方法、`isAssignableFrom()`方法、`isInstance()`方法、`instanceof`关键字等判断出来的结果。 

### 类加载器种类

启动类加载器，Bootstrap ClassLoader，加载JACA_HOME\lib，或者被-Xbootclasspath参数限定的类
扩展类加载器，Extension ClassLoader，加载\lib\ext，或者被java.ext.dirs系统变量指定的类
应用程序类加载器，Application ClassLoader，加载ClassPath中的类库
自定义类加载器，通过继承ClassLoader实现，一般是加载我们的自定义类 

### 双亲委派模型

类加载器 Java 类如同其它的 Java 类一样，也是要由类加载器来加载的；除了启动类加载器，每个类都有其父类加载器（父子关系由组合（不是继承）来实现）；

所谓双亲委派是指每次收到类加载请求时，先将请求委派给父类加载器完成（所有加载请求最终会委派到顶层的Bootstrap ClassLoader加载器中），如果父类加载器无法完成这个加载（该加载器的搜索范围中没有找到对应的类），子类尝试自己加载。

![img](https://images2015.cnblogs.com/blog/879896/201604/879896-20160415085506488-408997874.png)

**双亲委派好处**

- 避免同一个类被多次加载；
- 每个加载器只能加载自己范围内的类；



### 类加载过程

类加载分为三个步骤：**加载**，**连接**，**初始化**；

如下图 , 是一个类从加载到使用及卸载的全部生命周期，图片来自参考资料；

![img](https://images2015.cnblogs.com/blog/879896/201604/879896-20160414224549770-60006655.png)

#### 加载

根据一个类的全限定名(如cn.edu.hdu.test.HelloWorld.class)来读取此类的二进制字节流到JVM内部;

将字节流所代表的静态存储结构转换为方法区的运行时数据结构（hotspot选择将Class对象存储在方法区中，Java虚拟机规范并没有明确要求一定要存储在方法区或堆区中）

转换为一个与目标类型对应的java.lang.Class对象；

#### 连接

**验证**

验证阶段主要包括四个检验过程：文件格式验证、元数据验证、字节码验证和符号引用验证;

**准备**

为类中的所有静态变量分配内存空间，并为其设置一个初始值（由于还没有产生对象，实例变量将不再此操作范围内）；

**解析**

将常量池中所有的符号引用转为直接引用（得到类或者字段、方法在内存中的指针或者偏移量，以便直接调用该方法）。这个阶段可以在初始化之后再执行。

#### 初始化

 在连接的准备阶段，类变量已赋过一次系统要求的初始值，而在初始化阶段，则是根据程序员自己写的逻辑去初始化类变量和其他资源，举个例子如下：

```
    public static int value1  = 5;
    public static int value2  = 6;
    static{
        value2 = 66;
    }
```

在准备阶段value1和value2都等于0；

在初始化阶段value1和value2分别等于5和6；

- 所有类变量初始化语句和静态代码块都会在编译时被前端编译器放在收集器里头，存放到一个特殊的方法中，这个方法就是<clinit>方法，即类/接口初始化方法，该方法只能在类加载的过程中由JVM调用；
- 编译器收集的顺序是由语句在源文件中出现的顺序所决定的，静态语句块中只能访问到定义在静态语句块之前的变量；
- 如果超类还没有被初始化，那么优先对超类初始化，但在<clinit>方法内部不会显示调用超类的<clinit>方法，由JVM负责保证一个类的<clinit>方法执行之前，它的超类<clinit>方法已经被执行。
- JVM必须确保一个类在初始化的过程中，如果是多线程需要同时初始化它，仅仅只能允许其中一个线程对其执行初始化操作，其余线程必须等待，只有在活动线程执行完对类的初始化操作之后，才会通知正在等待的其他线程。(所以可以利用静态内部类实现线程安全的单例模式)
- 如果一个类没有声明任何的类变量，也没有静态代码块，那么可以没有类<clinit>方法；

**何时触发初始化**

1. **为一个类型创建一个新的对象实例时（比如new、反射、序列化）**
2. **调用一个类型的静态方法时（即在字节码中执行invokestatic指令）**
3. **调用一个类型或接口的静态字段，或者对这些静态字段执行赋值操作时（即在字节码中，执行getstatic或者putstatic指令），不过用final修饰的静态字段除外，它被初始化为一个编译时常量表达式**
4. **调用JavaAPI中的反射方法时（比如调用java.lang.Class中的方法，或者java.lang.reflect包中其他类的方法）**
5. **初始化一个类的派生类时（Java虚拟机规范明确要求初始化一个类时，它的超类必须提前完成初始化操作，接口例外）**
6. **JVM启动包含main方法的启动类时。** 



### 卸载

JVM中的Class只有满足以下三个条件，才能被GC回收，也就是该Class被卸载（unload）：

  \- 该类所有的实例都已经被GC，也就是JVM中不存在该Class的任何实例。
  \- 加载该类的ClassLoader已经被GC。
  \- 该类的java.lang.Class 对象没有在任何地方被引用，如不能在任何地方通过反射访问该类的方法



## 对象创建过程

![img](https://img2020.cnblogs.com/blog/1806053/202012/1806053-20201210160526521-28292277.png)

1）**类加载检查：**

　　JVM检查：1. 能否在常量池中定位 类的符号引用？ 2.类是否被加载、解析、初始化过？

2）**分配内存：**

　　从堆中分配内存；方式有1.指针碰撞 2.空闲列表

![img](https://img2020.cnblogs.com/blog/1806053/202012/1806053-20201210161508048-1192304958.png)

![img](https://img2020.cnblogs.com/blog/1806053/202012/1806053-20201210161547373-1653785971.png)

 　内存分配并发问题（线程安全）：

 　　　1. CAS+失败重试。CAS是乐观锁，遇到失败就不断重试。

　　　　 2. TLAB。为每个线程预先分配一块内存，当TLAB内存不够用时，再采用CAS方法分配。

 3）**初始化零值：**

　　 将分配的内存全初始化为0（不包括对象头），这样直接可用

 4）**设置对象头：**

　　对象信息存放在对象头中。1. hashCode、GC分代年龄、锁状态标志  2. 对象指向它的类的指针 

 5）**执行init方法：**

 　 按照java程序进行init 初始化





## 对象生命周期

对象的整个生命周期大致可以分为7个阶段：创建阶段（Creation）、应用阶段（Using）、不可视阶段（Invisible）、不可到达阶段（Unreachable）、可收集阶段（Collected）、终结阶段（Finalized）与释放阶段（Free）。

- 垃圾回收器发现该对象已经不可到达。
- finalize方法已经被执行。
- 对象空间已被重用。

当对象处于上面的三种情况时，该对象就处于可收集阶段、终结阶段与释放阶段了。虚拟机就可以直接将该对象回收了。



## 垃圾回收

[JVM的垃圾回收机制 总结(垃圾收集、回收算法、垃圾回收器) - aspirant - 博客园 (cnblogs.com)](https://www.cnblogs.com/aspirant/p/8662690.html)

JVM的内存结构包括五大区域：程序计数器、虚拟机栈、本地方法栈、堆区、方法区。其中程序计数器、虚拟机栈、本地方法栈3个区域随线程而生、随线程而灭，因此这几个区域的内存分配和回收都具备确定性，就不需要过多考虑回收的问题，因为方法结束或者线程结束时，内存自然就跟随着回收了。而Java堆区和方法区则不一样，这部分内存的分配和回收是动态的，正是垃圾收集器所需关注的部分。

垃圾收集器在对堆区和方法区进行回收前，首先要确定这些区域的对象哪些可以被回收，哪些暂时还不能回收，这就要用到判断对象是否存活的算法。



**引用计数法**

引用计数是垃圾收集器中的早期策略。在这种方法中，堆中每个对象实例都有一个引用计数。当一个对象被创建时，就将该对象实例分配给一个变量，该变量计数设置为1。当任何其它变量被赋值为这个对象的引用时，计数加1（a = b,则b引用的对象实例的计数器+1），但当一个对象实例的某个引用超过了生命周期或者被设置为一个新值时，对象实例的引用计数器减1。任何引用计数器为0的对象实例可以被当作垃圾收集。当一个对象实例被垃圾收集时，它引用的任何对象实例的引用计数器减1。

**优点**：引用计数收集器可以很快的执行，交织在程序运行中。对程序需要不被长时间打断的实时环境比较有利。

**缺点**：无法检测出循环引用。如父对象有一个对子对象的引用，子对象反过来引用父对象。这样，他们的引用计数永远不可能为0。

### **可达性分析法**

可达性分析算法是从离散数学中的图论引入的，程序把所有的引用关系看作一张图，从一个节点GC ROOT开始，寻找对应的引用节点，找到这个节点以后，继续寻找这个节点的引用节点，当所有的引用节点寻找完毕之后，剩余的节点则被认为是没有被引用到的节点，即无用的节点，无用的节点将会被判定为是可回收的对象。

可以作为 GC ROOT 的对象

- 虚拟机栈中引用的对象
- 本地方法栈中 JNI(即一般说的Native方法)引用的对象
- 本地方法区中
  - 类静态属性引用的对象
  - 常量引用的对象



方法区中的Class只有满足以下三个条件，才能被GC回收，也就是该Class被卸载（unload）：

  \- 该类所有的实例都已经被GC，也就是JVM中不存在该Class的任何实例。
  \- 加载该类的ClassLoader已经被GC。
  \- 该类的java.lang.Class 对象没有在任何地方被引用，如不能在任何地方通过反射访问该类的方法



### GC算法



**标记/清除**

标记需要清除的对象然后清除。

**缺点**

- 效率：标记和清除的效率都不高
- 空间：清理后会产生大量的不连续的内存，之后分配大内存对象时，不得不提前触发垃圾回收



**标记/复制**

将内存分为两块，每次只使用其中一块。每次垃圾回收时，将存活的对象复制到另一块，然后清理那块全部空间。

比较适合可以大量进行垃圾回收的新生代。

**缺点**

- 内存占用较多



**标记/整理**

标记过程一样，就是清除的时候，将所有活着的对象移到一端。然后清理剩下的区域

**缺点**

-  回收效率不高。

> 所以一般用在老年代的回收



### 分代收集

分代收集算法是目前大部分JVM的垃圾收集器采用的算法。它的核心思想是根据对象存活的生命周期将内存划分为若干个不同的区域。一般情况下将堆区划分为老年代（Tenured Generation）和新生代（Young Generation），在堆区之外还有一个代就是永久代（Permanet Generation）。老年代的特点是每次垃圾收集时只有少量对象需要被回收，而新生代的特点是每次垃圾回收时都有大量的对象需要被回收，那么就可以根据不同代的特点采取最适合的收集算法。

目前大部分垃圾收集器对于**新生代都采取Copying算法**，因为新生代中每次垃圾回收都要回收大部分对象，也就是说需要复制的操作次数较少**，但是实际中并不是按照1：1的比例来划分新生代的空间的，一般来说是将新生代划分为一块较大的Eden空间和两块较小的Survivor空间（一般为8:1:1），每次使用Eden空间和其中的一块Survivor空间，当进行回收时，将Eden和Survivor中还存活的对象复制到另一块Survivor空间中，然后清理掉Eden和刚才使用过的Survivor空间**。

而由于**老年代的特点是每次回收都只回收少量对象，一般使用的是Mark-Compact算法。**

#### 年轻代



a) 所有新生成的小对象首先都是放在年轻代的。年轻代的目标就是尽可能快速的收集掉那些生命周期短的对象。

b) 新生代内存按照8:1:1的比例分为一个eden区和两个survivor(survivor0,survivor1)区。一个Eden区，两个 Survivor区(一般而言)。大部分对象在Eden区中生成。回收时先将eden区存活对象复制到一个survivor0区，然后清空eden区，当这个survivor0区也存放满了时，则将eden区和survivor0区存活对象复制到另一个survivor1区，然后清空eden和这个survivor0区，此时survivor0区是空的，然后将survivor0区和survivor1区交换，**即保持survivor1区为空(美团面试，问的太细，为啥保持survivor1为空，答案：为了让eden和survivor0 交换存活对象)**， 如此往复。当Eden没有足够空间的时候就会 触发jvm发起一次Minor GC

c) 当survivor1区不足以存放 eden和survivor0的存活对象时，就将存活对象直接存放到老年代。若是老年代也满了就会触发一次Full GC(Major GC)，也就是新生代、老年代都进行回收。

d) 新生代发生的GC也叫做Minor GC，MinorGC发生频率比较高(不一定等Eden区满了才触发)。

#### 年老代

a) 在年轻代中经历了N次垃圾回收后仍然存活的对象，或是新生成的大对象，就会被放到年老代中。因此，可以认为年老代中存放的都是一些生命周期较长的对象。

b) 内存比新生代也大很多(大概比例是1:2)，当老年代内存满时触发Major GC即Full GC，Full GC发生频率比较低，老年代对象存活时间比较长，存活率标记高。



所谓的新生代和老年代是针对于分代收集算法来定义的，新生代又分为Eden和Survivor两个区。加上老年代就这三个区。数据会首先分配到Eden区 当中（当然也有特殊情况，如果是大对象那么会直接放入到老年代（大对象是指需要大量连续内存空间的java对象）。），当Eden没有足够空间的时候就会 触发jvm发起一次Minor GC。如果对象经过一次Minor GC还存活，并且又能被Survivor空间接受，那么将被移动到Survivor空 间当中。并将其年龄设为1，对象在Survivor每熬过一次Minor GC，年龄就加1，当年龄达到一定的程度（默认为15）时，就会被晋升到老年代 中了，当然晋升老年代的年龄是可以设置的。如果老年代满了就执行：Full GC 因为不经常执行，因此采用了 Mark-Compact算法清理

其实新生代和老年代就是针对于对象做分区存储，更便于回收等等



## String

String：不可变[字符串](https://so.csdn.net/so/search?q=字符串&spm=1001.2101.3001.7020)；

[StringBuffer](https://so.csdn.net/so/search?q=StringBuffer&spm=1001.2101.3001.7020)：可变字符串、效率低、线程安全；

StringBuilder：可变字符序列、效率高、线程不安全；

（1）如果要操作少量的数据用 String；

（2）多线程操作字符串缓冲区下操作大量数据 StringBuffer；

（3）单线程操作字符串缓冲区下操作大量数据 StringBuilder（推荐使用）。



```java
String str=new String("abc");
```

1. 首先，我们看到这个代码中有一个`new`关键字，我们知道**new**指令是创建一个类的实例对象并完成加载初始化的，因此这个字符串对象是在**运行期**才能确定的，创建的字符串对象是在**堆内存上**。
2. 其次，在String的构造方法中传递了一个字符串`abc`，由于这里的`abc`是被`final`修饰的属性，所以它是一个字符串常量。在首次构建这个对象时，JVM拿字面量`"abc"`去字符串常量池试图获取其对应String对象的引用。于是在堆中创建了一个`"abc"`的String对象，并将其引用保存到字符串常量池中，然后返回；

所以，这里正确的回答应该是： 如果`abc`这个字符串常量不存在，则创建两个对象，分别是`abc`这个字符串常量，以及`new String`这个实例对象。

如果`abc`这字符串常量存在，则只会创建一个对象。





## 堆的并发内存分配

一、CAS + 自旋

CAS是一种乐观锁的实现方式，每次不加锁假设没有冲突的去完成某项操作，如果因为冲突导致操作失败就重试，直到成功为止。

二、TLAB

TLAB (Thread Local AllocationBuffer,线程本地分配缓冲区)。

TLAB是在Java堆空间划分出来的针对每个线程的内存空间，专门在该区域为该线程创建的对象分配内存。

TLAB仅作用于新生代的 Eden Space，对象被创建的时候首先放到这个区域，但是新生代分配不了内存的大对象会直接进入老年代。

TLAB本质上还是在 Java 堆中的，所以在 TLAB 区域的对象，也可以被其他线程访问。

使用了 TLAB 之后，JVM 会针对每个线程在堆内存中预留一个内存区域，在预留这个操作发生的时候，需要进行加锁或者采用 CAS 等操作进行保护，避免多个线程预留同一个区域。

一旦确定了某个区域分配给某个线程，之后该线程需要分配内存的时候，会优先在这片区域申请。只是在“分配”这个动作上是线程独占的，至于在读取、垃圾回收等动作上都是线程共享的，因此在分配的时候不用进行加锁等操作，从而既保护了线程安全又提升了分配速度。





## 设计模式



### 单例模式

单例模式确保某个类只有一个实例，而且自行实例化并向整个系统提供这个实例。

**特点**

- 单例类只能有一个实例。
- 单例类必须自己创建自己的唯一实例。
- 单例类必须给所有其他对象提供这一实例。

**饿汉式**

饿汉式单例模式只要调用了该类，就会实例化一个对象，但有时我们并只需要调用该类中的一个方法，而不需要实例化一个对象，所以饿汉式是比较消耗资源的。

```java
public class Singleton {
    private static Singleton ourInstance;
    
    static {
         ourInstance = new Singleton();
    }

    public static Singleton getInstance() {
        return ourInstance;
    }

    private Singleton() {}
}
```

**懒汉式**

```java
public class Singleton {
    //volatile的作用是：保证可见性、禁止指令重排序，但不能保证原子性
    private volatile static Singleton ourInstance;

    public static Singleton getInstance() {
        if (null == ourInstance) {
            synchronized (Singleton.class) {
                if (null == ourInstance) {
                    ourInstance = new Singleton();
                }
            }
        }
        return ourInstance;
    }

    private Singleton() {
    }
}
```



### 模板模式

父类定义整个处理流程，子类实现具体步骤。



**登场角色**

- AbstractClass（抽象类）

AbstractClass 角色不仅负责实现模板方法，还负责声明在模板方法中所使用到的抽象方法。这些抽象方法由子类 ConcreteClass 角色负责实现。

- ConcreteClass（具体类）

该角色负责具体实现 AbstractClass 角色中定义的抽象方法。这里实现的方法将会在 AbstractClass 角色的模板方法中被调用。



**优点**

在父类的模板方法中编写了算法，因此无需在每个子类中再编写算法。



**一致性**

运用多态，将子类的实例保存在父类的变量中，再来调用display。即使没有用 instanceof 等指定子类的种类，程序也能正常工作。

无论在父类类型的变量中保存哪个子类的实例，程序都可以正常工作，这种原则称为 LSP。





### 工厂模式

在父类中规定处理的流程，在子类中实现具体的处理模式。父类决定实例的生成方式，具体的处理全部交给子类负责。这样可以将生成实例的框架（framework）和实际负责生成实例的类解耦。



**登场角色**

- Product（产品）

Product 角色属于框架这一方，是一个抽象类。它定义了在 Factory Method 模式中生成的那些实例所持有的接口（API），但具体的处理则由子类 ConcreteProduct 角色决定。

- Creator（创建者）

Creator 角色属于框架这一方，它是负责生成Product角色的抽象类，但具体的处理则由子类 ConcreteCreator 角色决定。

Creator 角色对于实际负责生成实例的 ConcreteCreator 一无所知，它唯一知道的就是，只要调用 Product 角色和生成实例的方法，就可以生成 Product 的实例。

**不用 new 关键字来生成实例，而是调用生成实例的专用方法来生成实例，这样就可以防止父类与其他具体类耦合。**

- ConcreteProduct（具体的产品）

ConcreteProduct 角色属于具体加工这一方，他决定了具体的产品。

- ConcreteCreator（具体的创建者）

ConcreteCreator 角色属于具体加工这一方，他负责生成具体的产品。



**优点**

使用已有的框架生成全新的类时，也完全不需要对 framework 进行修改。
