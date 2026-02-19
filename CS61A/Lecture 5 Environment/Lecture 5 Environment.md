接受另一个函数作为参数值 或者return另一个函数的函数

**Nested Definition**
```python
def make_adder(n):
	def adder(k):
		return k + n
	return adder
	
add_three = make_adder(3)
add_three(4)
```
Global frame

make_adder(第一步调用就在全局框架下调用了make_adder)

add_three（在函数定义后 全局中， 把函数make_adder(3)绑定到add_three上）

Frame1: make_adder(第二次调用来自make_adder框架下的 是对make_adder框架下的调用)
	n（第一个参数 make_adder自身携带的n)
	adder(第二个参数)
	return value 框架下的返回值 返回adder(k)
Frame2: adder 他的父框架是make_adder
	k adder函数框架下的参数k
	return value 
	
![[Frame Explantion.png]]
一个函数被创建的时候 他的parent就是创建这个函数的当前frame
在这个parent frame中 创建的下级函数名 绑定了 这个下级函数值
人话翻译（当函数被调用时）
	1.添加一个local frame 用来装这个函数
	2.给这个local frame添加一个父条目 告诉这个函数 如果你找不到变量了 你去哪里找
	3.找到变量后 把形式参数 绑定到找到的实际参数上
	4.运行这个函数

**Function Composition函数复合**
```python
def twice(f, x):
    return f(f(x))
    
def square(x):
    return x**2
    
def triple(x):
    return x**3
    
def compose(f, g):
    def h(x):
        return f(g(x))
    return h
    
result = twice(square, 2)
```
可以写compose(f, g)(x) 代表fg是compose的原参数 x是要传给子函数h的参数

**Lambda Expression**
无需多次定义该函数--但是只能定义很简短的函数 不能定义复杂逻辑的函数

E.g: square = lambda x: x * x  可以随时写在函数里调用 而无需创建复杂的复合函数

lambda和def 的environment diagram本质上是不同的

**Currying函数柯里化**

```python
def curry2(f):
	def g(x):
		def h(y):
			return f(x, y)
		return h
	return g
```
 
什么是Curry化-- 把一个接受多个函数的大函数 变成一连串接受一个参数的函数

可以理解为f(x, y, z, ....)---->f(x)(y)(z)(....)