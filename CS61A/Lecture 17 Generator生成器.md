# `yield`关键字

yield可以看成一个惰性的return 把“返回值“塞到一个惰性的迭代器之中
yield的应用常常和**递归生成器**相关 比如树的处理
一个常见的**递归生成器**模板：
```python
def gene_func(n):
	###Basic Case###
	###操作###
	for ways in gene_func(f(n)):
		###操作###
		yield [操作产物] + ways
```
上面这个模板是要求对数据进行修改的 下面的这个使用了**yield from**语法 
```python
def gene_func(n):
	###Basic Case###
	###操作###
	yield from gene_func(f(n))
```
yield from是一个语法糖 本质上和上面的loop interpret出来的是一样的
还有一个注意点 from会生成一个return值 而正常写loop是不会有返回值的

生成器函数也可以用return  在找到value之后直接return 就只返回这一条路径