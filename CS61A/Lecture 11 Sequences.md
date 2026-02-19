
#### List
```python
from operator import getitem

getitem(digits, 3)
#Effects equal digits[3]
```

List可以进行加减乘除 但是不管如何 都不会影响里面的元素  比如：
`[2, 7] + digits*2 (digits = [1,2,3])` ==
`[2,7,1,2,3,1,2,3]` 加到末尾 乘号是变成两倍
List没有元素种类要求 什么都可以

#### Containers
用来评估一个数到底是不是在一个List中 本质上是遍历List的所有元素 O(n) & O(n)
`--1 in digits -- True`
只能评估单个元素 而且不能带单引号 他就是数据 不是字符或者字符串

#### For Statements

in的内容不局限在range() 只要是一个sequence表达式 就支持调用

Python的for不产生独立的Block作用域 
这个for循环的i会在当前的frame中持续存在 可以一直调用 
不同于java或者cpp 这两者在Block结束之后立即销毁这个变量i
本质上是python的语言精度处在function级别 其他处在block级别

py-for支持**sequence unpacking**
比如我有一个pairs-List 里面储存了很多组数对
可以这么写：
```python
for x, y in pairs:
	if x == y:
		func1()
		......
```

**Iteration Value**

Range - Sequence Not List
连续整数数列 左闭右开--
```python
for i in range(5)选择长度
#0 1 2 3 4
for i in range(-1, 3)选择区间
# -1 0 1 2
```

#### List Comprehension

用for的单个语句直接从一个list中抓取一部分元素
```python
odds = [1,2,3,4,5]
[x + 1 for x in odds]
[x for x in odds if 25 % x == 0]
```

```python
def divisors(n):
	return [1] + [x for x in range(1, n + 1) if n % x == 0]
```
