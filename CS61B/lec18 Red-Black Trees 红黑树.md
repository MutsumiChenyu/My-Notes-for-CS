
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
