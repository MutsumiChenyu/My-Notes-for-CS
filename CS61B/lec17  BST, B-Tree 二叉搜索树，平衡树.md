logN - class 树越茂密 数据节点越多 实现的性能越好
Binary-Search-Tree BST 一棵树
对于这棵树上的每一个节点 他左边的节点都小于他 右边的节点都大于他

#### Insert in the BST
代码实现
```java
public BST insert(BST tree, int key){

	/*Base Case 当树空了 我们做什么*/
	if (T == null){
		return new BST(key);
	/*Second Case key大 走右边*/
	}else if (T.key < key){
		T.right = insert(T.right, key);
	/*Third Case key小 走左边*/
	}else if (T.key > key){
		T.left = insert(T.left, key);
	/*Final Case key相等 不插入*/
	}else{
		return;
	}
}
```

#### Delete in the BST
代码实现
```java
public BST delete(BST T, key){

}
```
删除一个具有两个子节点的节点的操作：
需要寻找到一个Predecessor（继任者）
继任者的寻找规则：Root（被删除的节点）的：
**左子树的最右侧的节点 或者是 右子树的最左侧的节点**


#### Using BST in Sets and Maps
in Lab

### B-Trees 分裂树 平衡树

#### Avoid Imbalance 
分裂树通过在每一个节点限制元素个数（如2， 3）来降低树的高度 达成近似log级别的时间复杂度
如图所示：
1. 19被加入到16，17，18中 --- 大小溢出！
2. pop掉 左侧+右边的内容 --- 17！
3. 把17加入上一层节点！
4. 16， 18， 19中 16不能存在于17右侧
5. 把16作为单独的节点分裂
![[BTree的分裂.png]]
如果父节点也满了 就继续向上生长 直到最上层的总Root节点

![[总节点分裂.png]]root节点满了 操作：
1. pop out左侧右边的元素 --- 17
2. 分裂13节点和后面的节点
3. 17作为总根连接这两个分裂节点

#### B-Tree的不变量
1. 树的深度由根节点上升增加 所有**叶子**始终保持在一个深度不变
2. 拥有K的元素的节点拥有K+1个分节点