
print 函数返回 None
复合函数的frame结构

```python
def delay(arg):
	print( 'delayed' )
	def g():
		return arg
	return g
```
这样一个函数 输入delay（delay）（）（6）（）会得到什么？
delay(delay)()(6)()
**具体嵌套操作如下：**
**delay(delay)**
先打印一个 delayed
再把arg = delay传到g()里面 返回了一个g()
**delay(delay)()**
g()作用于（） 无效果 返回了一个g
**delay(delay)()(6)**
g(6) 返回一个6（这是返回值）
**delay(delay)()(6)()**
无效果

最终成果： delayed \n delayed || 返回值：（6）

**print(delay(print) () (4) )**
第一步先分析大print里面的东西-- delay 打印一个delayed 然后返回一个函数g
第二步是g() 返回刚才存储的arg  也就是print
第三步是 print（4） 先打印一个4 然后返回None
最后是用大print来返回上面的所有东西 delayed 4 None

```python
def delay(arg):
	print( 'delayed' )
	def g(arg): #不同之处 这边的arg是g的参数 读取不到上面的arg
		return arg
	return g
```


Example
```python
def horse(mask):
	horse = mask #这里的horse是变量 和传入的变量mask相符合
	def mask(horse): #这里的mask是函数 这里的horse是刚才的变量 他的值和mask这个最初传入的变量相等
		return horse #这里的horse是参数horse
	return horse(mask)

mask = lambda horse: horse(2)#这里是真的 在Global Frame里面的mask 要在后面的函数中被调用的

horse(mask)
```

具体的内部结构逻辑：
```
return horse(mask)
       │      │
       │      └─ 内部函数: def mask(horse): return horse
       │
       └─ lambda horse: horse(2)
↓ 展开调用
(lambda horse: horse(2))(mask)
↓ lambda 参数 horse 绑定为 mask
horse(2)  # 此时 horse = mask
↓ 即
mask(2)
↓ 内部函数 mask 接收 2
def mask(horse):  # horse = 2
    return horse  # return 2
↓ 结果
2
```


```python
(lambda x : x(2))(A) = A(2) #参数转发器 把lambda的参数转发到A上
一个以函数作为参数的函数
```