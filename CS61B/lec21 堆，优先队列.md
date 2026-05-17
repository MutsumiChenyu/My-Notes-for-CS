
#### Priority Deque
优先队列的要素：双端队列+每次都给出一个最小的（Comparable）元素
```java
/** 最小优先队列: Allowing tracking and removal of 
  * the smallest item in a priority queue. */
public interface MinPQ<Item> {
    /** Adds the item to the priority queue. */
    public void add(Item x);
    /** Returns the smallest item in the priority queue. */
    public Item getSmallest();
    /** Removes the smallest item from the priority queue. */
    public Item removeSmallest();
    /** Returns the size of the priority queue. */
    public int size();
}
```
不必用一整个列表实现数据结构，节省空间
比如要找到一系列数据中最大的10个样本点，每次总数达到10个之后，下一次添加变成11个，随后立即执行removeSmallest的操作，保证利用的内存空间只有常数级别

#### 实现
有序数组，BST，Hash Table都不够优雅

#### Binary Min Heap 二叉最小堆
仍然是一棵树的实现形式 但是这里的每个节点都**小于**他的两个子节点

缺失的节点必须位于底层，这棵树是complete的 同时这棵树的元素尽可能左倾

每次的最小内容都是树根 pop内容较为简单

##### 加入元素
每次把加入的元素放在最底层的靠近左侧的第一个空格
然后进行fix and swap 让这个树最终达成这些条件
一路从叶子走到根

##### 删除元素
每次删除的都是最小元素--也就是根节点
处理方法：把最底层最左侧的一个元素 直接放到根节点的位置 然后继续进行fix and swap
每次这个swap都要从上往下往最小的元素进行交换
从根往叶片推广

#### 基于数组的树实现
```java
public class arrayTree<T>{
	T[] content;
	int[] parents;
}
```
content这个元素代表key 每一个数组内存格子储存一个对应的数据内容
parents这个元素代表映射 每一个内存格储存了 对应index对应的content内容的这个元素 的父节点是什么 （根节点就是自身）
其实无需parents 只需要自身的（（index - 1） / 2）就可以直接得到这个节点的父节点
同时这个数组写一个resize的功能即可

#### 代码实现
```java
public class heap
```