表示层次关系 

## 理解递归的最好方式：

**想象自己也是一个节点，自己参与这个函数的循环。然后你只需要知道 我接受什么信息，我给出什么信息就行了，千万不要在脑子里堆栈**
举个例子：比如HW4的最后一题

**我作为一个节点需要知道什么？ 这些：**
**我接受一棵树 这个树来自我的父节点。如果这棵树退化成一片叶子，那么我就返回它的标签值。 如果这棵树是完整的 那我只需要指挥我的手下干这些事：把你们下面的最大值给我算出来给我知道，至于他们具体做了什么，我不在乎。 最终我的返回值就是我的几个手下汇报给我的最大值中间的最大值，再加上我自己的标签值，传递给我的老板，只需要考虑我的直系上司和直系下属就可以进行。 这才是递归的真正理解方式



Tree拥有两个要素 **Root Label 和 Branches**
每一个Branch也是一个Tree

每一个点称为`Node`
![[Pasted image 20260130222059.png||600]]

#### Tree的代码实现（构造模式）
```python
#Constructor 构建数据结构
def tree(label, branches=[]):#定义一个构造树函数
	for branch in branches:
		assert is_tree(branch)#断言语句
	return [label] + list(branches)
	
	#树的形式：
	tree(1, [2, [leaf2, leaf3]])

# Selector	找到数据结构包含的某几种数据要素
def label(tree):
	return tree[0]
	
def branches(tree):
	return tree[1:]	
	
#Validator 验证器
def is_tree(tree):
	if type(tree) != list or len(tree) < 1:
		return False
	for branch in branches(tree):
		if not is_tree(branch):
			return False
	return True
```

# 严肃注意一下这个写法

**`for b in branches(tree):`
**最快最好的遍历子树的方法 前提是树是用label-branch写法写出来的**
#### Tree的Recursion实现
```python
def fib_tree(n):
	if n <= 1:
		return tree(n)
	else:
		left, right = fib_tree(n - 2), fib_tree(n - 1)
		#左侧小于右侧
		return tree(label(left) + label(right), [left, right])
		
#这个树的root 是left + right的label之和 这个树的branches是先走遍左侧的子节点 再走遍右侧的子节点
```
##### 用递归来处理一棵树的数据
```python
def count_leaf(tree):
	if is_leaf(tree):
		return 1
		#遍历到了最深的一层 如果他是一片叶子 没有分支 那么就返回1 这是递归的终点 回复的起点
	else:
		branch_count = [count_leaf(b) for b in branches(tree)]
		#核心递归部分
		return sum(branch_count)
```

总之就是一直走分支 然后思路一般是从左往右走