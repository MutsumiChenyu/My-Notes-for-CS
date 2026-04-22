
#### Priority Deque
优先队列的要素：双端队列+每次都出一个最小元素
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

目的：考察各个数据结构移除和加入最小元素的空间复杂度和时间复杂度
