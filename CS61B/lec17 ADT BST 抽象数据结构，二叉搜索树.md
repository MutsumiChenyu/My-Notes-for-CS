
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

