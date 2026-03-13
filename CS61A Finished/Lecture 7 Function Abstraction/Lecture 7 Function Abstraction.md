
### Lambda Function

Parent是lambda函数所处的当前frame

![[Pasted image 20251127214414.png|600]]
a  = 1 是全局的a a = 2是f的local frame下面的a

### Return

结束在当前函数的local frame的调用 返回一个值同时返回到上一级的frame
```python
def search(f):
	x = 0
	while True:
		if f(x):
			return x
		x+=1
def is_three(x):
	return x == 3#这是一个比较表达式 最后return的是后面式子的结果（bool型） True or False
	
```


### Abstraction

![[Pasted image 20251127223211.png]]
调用函数需要知道 参数 和 函数的运算结果
不需要知道函数名和具体的调用运算逻辑的

### Choose a name

### Which deserves name

### Error and Tracebacks

Syntax Problems 语法错误
Logical Error 逻辑错误
Type Error 类型错误

**如何解读回溯信息**

What File -- What line -- Where the wrong
![[Pasted image 20251127224241.png|400]]
一个括号打开了没关上 最终能追溯到def上 因为是def这里 在报错

又比如 调用了一个无返回值的函数 - 另一个函数 会报Type Error 因为None(Void)不能相减
