
**Multiple Environments**
 ```python
 from operator import mul
 def square():
	 return mul(x, x)
 suqare(square(3))
 ```
 Global frame: 1.mul 2.square(全局状态下的定义 )
 Frame1: square  (inside)
 Frame2: square  (outside)

**Miscellaneous Python Features 不同的Python特性**
 运算符如何工作：+ 代表调用函数 add  \*代表调用函数 mul
 / 真除法truediv  //整数除法floordiv %取模运算mod

**Python的文档测试doctest**
 ```python
 from operator import floordiv, mod

 def result(n, d):
     """"
     >>> q, r = result(2013, 10)  #注意">>>" 后面要加一个空格 不然不能使用
     >>> q
     201
     >>> r
     2
     """
     return floordiv(n, d),  mod(n, d)
 ```
 中间的这部分注释属于文档测试 doctest 
 可以在运行时自动检测文档测试是否符合这个函数应该有的输出结果

 或者说 在这个函数定义中 加入一个测试把参数传进去 看看是否符合 不影响这个函数后面的操作功能

**Conditional Statements条件语句**
 语句Statement
 复合语句跨越多行 从"："开始 一直到不再缩进的地方结束
 ```python
 if x < 0:
	 return -x
 elif x > 0:
	 return x
 else:
	 return 0
 ```

 Boolean contexts Bool上下文
 False values: False, 0, '', None

**Iteration迭代语句**
 ```python
 i, total = 0, 0
 while i < 3:
	 i = i + 1
	 total = total + i
 ```
 while 的逻辑
 1.先判断这个头表达式
 2.再判断这是 True or False 如果为True 那就执行完 再重复第一步
 Fibonacci Sequence
 ```python
 def fib(n)
	pred, curr = 0, 1 #pred前一个数 curr现在的数
	k = 1
	while k < n:
	pred, curr = curr, pred + curr
	k = k + 1
	return curr
 ```

**Control**
 两种表达式的对比
 一个常规if vs 一个设定好的if_(c, f, t)
 ```python
 def if_(c, f, t):
	 if c:
		return f
	 else:
		 return t
		
 def real_sqrt(x):
	 return if_(x >= 0, sqrt(x), 0)
	
 def real_sqrt2(x):
	 if x >= 0:
		 return sqrt(x)
	 else:
		 return 0
 ```
  事实上 这两个定义的real_sqrt的输出是不一样的

  在第一个函数定义中 一定是先执行if_中的东西 然后算出参数 再传到if_里面
  然后因为sqrt不能对负数计算 直接报错了

**Logical Expression**
 A **and** B 从A到B依次评估
 A **or** B

 例子
 ```python
 def reasonable(n):
	 return n == 0 or 1/n != 0
 ```

 断言语句 **Assert**
 assert AAA, 'BBB'
 在执行时 如果AAA为True 那他什么都不做
 如果AAA为False 那他就报错 并且提供一条信息：'BBB'