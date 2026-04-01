
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
