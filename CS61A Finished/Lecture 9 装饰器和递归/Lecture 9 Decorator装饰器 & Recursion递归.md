#### 装饰器写法：
`from ucb import trace`
`@trace`
......

```python
def trace1(fn):
	def trace(x):
		print('Calling', fn, 'on argument', x)
		return fn(x)
	return traced
	
#然后在下面接着定义函数 可以写 @trace1 来作为这个函数的装饰器

@trace1
def ABC():
```

@trace1 等同于 trace1(fn)
在函数定义的时候写@作为装饰器
先是函数的装饰器 然后是函数本体 可以清楚的知道我给函数加了哪些修饰

**装饰器干些什么**:
装饰器本身是一个高阶函数 对于你新定义的函数 本质上这个函数被你的装饰器作为一个参数接收 除了执行函数本身的内容外 要先执行装饰器的命令 比如打印日志 打印函数调用的过程

**解耦**
装饰器使用来解耦的元件 目的是分开不同功能

#### Self-Reference自指
一个函数返回自己的行为称为自指
```python
def print_all(x):
	print(x)
	return print_all
	
print(1)(3)(5)
```
先打印1 然后返回 再打印3 然后再返回 并且打印5

```python

def print_sum(x):
	print(x)
	def next_sum(y): #这个函数的意义就是告诉主函数 在下一次循环里面你要干什么事情
		return print_sum(x + y)
	return next_sum
	
print_sum(1)(3)(5)
```
这边的流程就是先打印1 然后接受3这个函数 返回一个print_sum(4) 然后打印一个4 返回一个print_sum(9) 最终打印了1 4 9
与上面的函数相比 这边的函数通过high-ordered的方式 来对下一次函数输出进行了指导
**用这样一个写法 来记忆自己输出了哪个数字 并且存在函数内部 可以进行进一步的叠加**

#### Recursive Functions递归函数

函数要么间接要么直接调用自己
不使用**循环** 但是对一个数字的各个位数 进行求和

```python
def split(n):
	return n // 10, n % 10

def sum_digits(n):
	if n < 10:
		return n
	else:
		last2, last = split(n) #last2是这边的剩余部分 last2再进去调用 一次一次最终执行完整个函数
		return sum_digits(last2) + last #称为一个TailCall 尾调用
```

#### Iteration vs Recursion
![[Pasted image 20251222221246.png]]
迭代是递归的一个特殊形式
迭代是需要传参的 需要一个参数继承 但是递归是不需要的 不需要创造一个新参数
比如上图中的**total k**这两个参数 在右侧的递归阶乘中完全不需要

#### 如何证明一个递归函数的有效性
其实是类似一个数学归纳法的理论 也是递归嘛

#### Mutual Recursion 两个函数的相互递归
**Luhn Algorithm**
这边有一个隔位的操作 一位\*2 一位不\*2
所以是 两个函数相互引用递归的
相互递归函数的示例：

```python
def is_even(n):
	if n == 0:
			return True
	else:
		return is_odd(n - 1)
def is_odd(n):
	if n == 1:
		return True
	else:
		return is_even(n - 1)
```
`一个数的奇偶判断`

`Luhn Algorithm`
![[Pasted image 20251222223356.png]]
##### 递归函数的结构
```python
def Recursion(A):
	#Most basic operation unit
	#这边是最小执行单元 描述的内容是当递归到最低点 函数要执行的人物
	
	return Recursion(A - 1)
	#这边返回往下走一层
```
