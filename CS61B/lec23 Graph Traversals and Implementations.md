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

![[BFS-Graph.png]]
以本图为例：
 1. s = 0 ，0元素入队，距离原点S = 0 距离dis = 0，对0执行操作， 检查到0的neighbour是1，0出队，1入队 当前队列[1]
 2. 当前节点 = 1，距离原点S = 0 距离dis = 1， 对1执行操作，检查到1的neighbour是2，4，1出队，2，4入队 当前队列[2, 4]
 3. 当前节点 = 2，距离原点S = 0 距离dis = 2， 对2执行操作，检查到2的neighbour是5，2出队，5入队 当前队列[4, 5]
 4. 当前节点 = 4，距离原点S = 0 距离dis = 2， 对4执行操作，检查到4的neighbour是3，5，1出队，3入队，5已经入队不再考虑 当前队列[5，3]
 5. 当前节点 = 5，距离原点S = 0 距离dis = 3， 对5执行操作，检查到5的neighbour是6，8，5出队，6，8入队 当前队列[3， 6， 8]
 6. 当前节点 = 3，距离原点S = 0 距离dis = 3， 对3执行操作，检查到3孤立，3出队 当前队列[6, 8]
 7. 当前节点 = 6，距离原点S = 0 距离dis = 4， 对6执行操作，检查到6的neighbour是7，6出队，7入队 当前队列[8, 7]
 8. 当前节点 = 8，距离原点S = 0 距离dis = 4， 对8执行操作，检查到8孤立，8出队，当前队列[7]
 9. 结束BFS
 
Some Attentions:

When you conduct BFS, you will record the current vertice is "edgeto" which parent and distance equals (dis of par + 1)
Distance in Graphs == Level in Trees