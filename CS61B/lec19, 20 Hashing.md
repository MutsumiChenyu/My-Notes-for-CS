避免对象必须要comparable

#### 解决问题
1. Memory Space -- 每个部分变成Linked Lists 以便于节约空间/快速扩容
2. N/M的扩容机制
3. 如何转化元素变成整数

#### 扩容机制 -- Sample as Integers

每个Hash：N个元素，M：模数/Hash Heap的数量， K：阈值 当K达到某一个特定的值时进行扩容操作
例如：0， 1， 2， 3｜｜M == 4， K = 1.5
。。。。。。

如果元素不是整数：在这个Hash类里面加一个方法 来把所有的元素打上一个整数标签 来进行Heap分类

以字符串为例：Base 26:
“cat” = square(26) \* 3 + 26 \* 1 + t
能够保证给每一个单词赋值一个唯一确定的与之对应的整数

#### 方法：hashCode()

原始数据--hash code--取模等运算--结果--填入Hash Table中
hashCode是根据内存地址计算的 最终导致每一次运行程序都会有完全不一样的结果

弊端：如果你创建了一个基于12的元素 原先的HashSet有X个元素，其中有一个Bucket包含了12 那么如果你要说这个HashSet包含了这个基于12的元素，P = 1/X
因此必须重写HashCode的编码方式

#### Mutability
一旦创建 无法改变
```java
public final int A;
//此处的A是一旦被确定值 就无法改变的final元素
```

如果是数组：
```java
public final Rocks[] rocks;
...
Rocks[1] = null; //Acceptable!
//之后可以进行修改Rocks中间的元素
```
