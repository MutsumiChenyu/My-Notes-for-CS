#### Objects & Methods
是OOP的核心 object-oriented-programming
objects是对象 Methods是方法 objects一般是结构体的小部分 Methods是内置的函数
比如：
```python
#这个就是Method
time.strftime()
#这个就是对象 month和year是object time是class
time.month
time.year
```
**Dot Expression**
Every value is a object and has attributes. 许多不同行为组合成的一个大对象

**ASCII**
![[Pasted image 20260203143946.png]]
**Unicode**
109000个字符 93个语言

#### Mutation Operations 变异行为
**以字符串为例**
```python
suits = ['A', 'B', 'C']
suits.pop()#移除末尾元素并且把他打印出来
suits.remove('C')#移除特定元素
suits.append('D')#添加特定元素
suits.extend('E', 'F')#从末尾添加多个特定顺序的元素
```
**以字典为例**
```python
numerals = {'I': 1, 'V': 5, 'X': 10}

numeral.pop()
numeral.get('X')
```

#### Tuples 元组
```python
tuple([3, 4, 5])
>>>(3, 4, 5)
```
元组是不可变类型 所以一个元组可以作为一个字典中的key
而List是不可以的 当然你的这个元素里不能包含一个List
**可变对象和不可变对象的差异**
![[Pasted image 20260203150010.png]]
元组 数字 字符这种类型是不可变类型 只能改变名称但是不可以改变对象性质 但是字符串 数组这些list类型是可以修改的， 属于可变类型

**Equal != Identical**
```python
a = [10]
b = [10]
a == b
>>> True
a is b
>>> False
```

#### Mutable Default Index
每一次默认参数都会绑定到上一次的输出结果上 导致默认参数变化 要用const

#### Mutable Function
一些函数表示了一些state 这些state变量 比如银行提款
**用高阶函数实现**
```python
def make_withdraw(balance):
	b = [balance]
	def withdraw(amount):
		if amount > b[0]
			return 'Error'
		else:
			b[0] = b[0] - amount
			return b[0]
	return withdraw
	
withdraw = make_withdraw(100)
```
这样写 这里的参数100就被永久记忆在了withdraw这个函数里面
他不会改变balance 但是会改变隐藏在函数内部的b
