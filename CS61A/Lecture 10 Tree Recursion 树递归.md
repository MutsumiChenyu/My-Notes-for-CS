
一个树递归的例子：
`斐波那契数列`
```python
def sequence(n):#n是我要找的数在斐波那契数列中的阶数
	if n == 1 or n == 2：
		return 1
	else:
		return sequence(n - 1) + sequence(n - 2)
```
Tree Recursion 指的是一个函数的递归会调用几次本身（使用不同的参数）

1-2-4-8......

##### Counting Partitions
计算整数的分区

##### 分治法
包括？ 不包括？两种思路 然后分别递归
```python
def count_partitions(n, m):
    # 1. 成功：正好凑到了 0
    if n == 0:
        return 1
    # 2. 失败：数字减多了，变成了负数
    elif n < 0:
        return 0
    # 3. 失败：还没凑完(n>0)，但已经没有可用数字了(m=0)
    elif m == 0:
        return 0
    # 递归步骤
    else:
        return count_partitions(n - m, m) + count_partitions(n, m - 1)
```

分治策略可以穷举出所有的排列方法

**方案总数**
**求子集的和**

比如：给定一个数组 请给出他的任意个数元素和 = 9的这种元素组的个数
先分两种 比如最后一个数是2 那我们就分析:
用2：前面的找个7
不用2：前面的找个9
然后一直递归到第一个数 来找方案

分治策略的本质是穷举，关心**全局最优** 与贪心算法不同，贪心更关注局部最优解
动态规划