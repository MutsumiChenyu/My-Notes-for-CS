#### Graph DFS

DFS的Pre/Post决定了如何处理节点
但是判定记录“边” 与DFS的顺序没有关联 判定边和深入递归是一体的 放在一起进行执行

#### Graph的编程实现

1. 映射矩阵实现 Adjacency Matrix (二维数组)
做一张表格 第一行和第一列都展示出所有元素 对应的格子表示这两个元素是否相连 0 or 1

在实践中Graph通常**Sparse**稀疏，这个实现方式的内存占用太大了
小特性：
无环图会产生一个symmetric的映射矩阵

2. 表示一组边 rare
3. 邻接链表 Adjacency List
Array of Lists

![[Graph实现.png]]
#### 实现的时间复杂度

V for vertices
E for edges

O(V + E) 哪一个元素增长快 哪一个元素占主导地位

#### BFS Breadth First Sort 广度优先搜索

图的BFS -- 根据**距离搜索原点S的距离**决定level数

