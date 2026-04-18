
Rotation 旋转树变换形态
#### Rotate

rotateLeft(G) -- if X is the right child of G, then->
after rotating, X is the root and X's left child becomes the right child of G.
任意一棵二叉搜索树都可以通过ON级别的时间复杂度变得平衡

#### Left leaning Black-red Tree 左倾红黑树

思路和23树一致 但是红黑树是使用BST实现的 因此要对1. 多元素共处一个节点 2. 有>2个字节点的情况产生
解决方案：添加一个新的连接类型-不是字节点-父节点的连接关系 是表示23tree的并列关系
这个连接类型是红色连接，P-C是黑色连接 红黑树
Left-leaning体现在分裂时把并列关系中小的元素放在大的元素的左边
每个23都对应一个LLRB 一一对应的关系 保证树平衡 同时RBT保证了可以完全用BST的dfs bfs进行搜索

#### LLRB的一些特性
1. 转化成23Tree必须平衡，转化式把红色连接放在一起即可
2. LLRB不能允许出现连续的Red Link

#### LLRB的构造与代码实现
**插入元素的时候** 无论插入的是什么 都用Red Link
在构造树的时候，**就进行不断的旋转和维护来保证树的丰满程度**

例子：此时不满足左倾的要求 对节点E执行左旋
![[Black-Red Tree.jpg|674]]
过饱和节点处理：ABC节点的拆分 LLRB就是BrA BlC
过饱和节点不需要进行旋转-->处理方法：
把这个过饱和节点的根节点相连的所有Link都反转颜色

**Insert核心逻辑：**
从插入位置依次往前回溯，执行如下操作直到达到Root：
1. 左旋 （if 当前节点Left红Right黑）
2. 右旋 （if 当前节点Left红 LeftChild的Left红）
3. 反转 （if 当前节点左右Link都Red， 反转颜色）
