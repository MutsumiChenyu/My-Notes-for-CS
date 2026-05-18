Tree 需要任意两个节点之间只有唯一一条路径连接

#### Tree Traversal
遍历一棵树的不同方式
![[DFS.png]]


Depth First Search
##### Pre-order DFS
DBACFEG
##### In-order DFS
ABCDFEG
##### Post-order DFS
ACBFEGD

#### 从图的角度，人类阅读树的方式

##### 前序
从root开始对一棵树进行逆时针画圈 
每当经过一个节点的左侧，就会读取这个节点的内容

从根节点开始 最右侧节点结束
##### 中序
从root开始对一棵树进行逆时针画圈 
每当经过一个节点底部就读取
从最左侧节点开始 最右侧结束
##### 后序
从root开始对一棵树进行逆时针画圈 
每当你经过一个节点的右侧就读取
从最左侧节点开始 根节点结束

#### Graph
一棵树两个节点之间可以有多条线路 Graph > Tree
Graph can be directed or undirected, which decides on the directions of edges.
And the edge can be numbered.
图有两个性质： **Whether directed and whether acyclic 是否有向 是否有环**
有向可能会改变一个图是否有环

##### Graphs Terminology:
Nodes == Vertices
Edges == adjacent == Connection
Path for a sequence of vertices connected by edges.
Simple path for no repeated vertices
Cycle for a path which has the same first and last vertices.
All vertices are connected, so the all graph is connected.
##### Simple Graph
1. No nodes connect to themselves 不自循环
2. No parallel edges connect the same nodes 不平行边

#### Graph Traversals

##### Q1 如何确定两点Connected？
每个节点问自己的neighbour 检查是否connected不断递归 同时检测过的节点进行mark防止infinite loop **深度优先搜索**
从左到右往右依次探索 深度优先探索整个subgraph

##### Q2 如何找到每一条路径
使用深度优先搜索

