在Java中 用Array而不是List实现一个和DLList功能相同的动态数组

#### 构建一个基于数组的列表

Java中的数组是不可变大小的， 为了用数组模拟列表， 采用每次添加新元素都复制一遍列表值的方法， 但是这种方式是简单遍历， 时间复杂度极高

#### Geometric Resizing

```java
public void insertBack(int x) {
	//先扩容
    if (size == items.length) {
           resize(size * RFACTOR);
    }
    //再把元素插入
    items[size] = x;
    size += 1;
}
```
与其添加数量 不如直接乘上一个因子倍数扩大数组的规模
resize是一个private的辅助方法

#### Memory Optimize
为了避免申请过多的内存块但是不使用 定义一个R = usage ratio使用率

一般来说， 当R == 0.25时， 减半大小

```java
public void Reduce(){
	if (size / items.length <= 0.25){
		resize(items.length / RFACTOR);
	}
}
```


#### 泛型AList
