
#### Bow and Pointer
环境图的应用
![[Pasted image 20260123104659.png||200]]
#### Slicing
从一个List中切除一部分的表示
`odds[1:3]` 表示 切出来 odds这个list的 第一个到第二个 左闭右开
`odds[1:] 1 2 3 4 ... Final`
`odds[:3] 0 1 2 
`odds[:] 表示索引全部数据`

**Slicing 总是创建新的值 复制 而不是指向 -->占内存**

#### Process Container Function
##### Sequence Aggregation

sum的起始值：
	`sum([2,3,4], 5)` = 5+2+3+4
	写法： `sum(iterable[, start]) --> value`
	第一个参数是一个可迭代对象 第二个参数是一个可选的起始值 可以是无 也可以是有
	**Attention**: 禁止用sum来连接字符串
	注意迭代部分的元素是什么种类
```python
# 情况 1：基础用法
sum([1, 2, 3])          # 结果是 6 (1+2+3，start 默认为 0)

# 情况 2：指定 start 参数
sum([1, 2, 3], 10)      # 结果是 16 (10 + 1+2+3)

# 情况 3：空列表
sum([], 5)              # 结果是 5 (列表为空，直接返回 start)

# 情况 4
sum([[2, 3], [4]],[])   # 结果：[2, 3, 4]
```
`[, start]` 用来对Python表示这个参数是可选的而不是必须的
##### `max`内置的keyfunc

对你的可迭代元素每一个应用一个函数 来算出实际的最大值

```python
max(range(10), key = lambda x: x ** 2 - 10 *x)
```
key = func(...)

##### all
all接受一个可迭代对象 如果这个迭代对象的每个元素都是True 则all返回True

```python
>>> all(range(5))

>>> True
```

#### String and Abstraction
三种字符串：
```python
''
""
"""ABCD
EFGHJKL
TYVBNJ
""" #这是一个跨多行的字符串

最后一行被打印出来的时候：
>>> 'ABCD\nEFGHJKL\nTYVBNJ'
```
使用了`\n`的转义字符 换行

值得注意的是：在一个字符串中提取一个元素 这个元素仍然是字符 而不是

列表里只能一个一个找 字符串里可以一串一串找

#### Dictionary

```python
{'key' : value}
```
字典的键值对 based on key 单向的

len(dict)

不能重复用key key不能是dict或者list
value可以有不同的种类 全部任意
多个值绑定一个key的常见方法：用key绑定一个List就行了

```python
numerals = {'I':1, 'V':5, 'X':10}
>>> numerals['X']
>>> 10
>>> numerals[10]
>>> Error
>>> list(numerals)
>>> ['I', 'V', 'X']
#那么如何索引字典的所有value呢？？？
>>> numerals.values()
>>> dict_values([1,5,10])
```
要想索引字典的所有值 他会先返还一个`dict_values` 里面包含了一个含有所有值的list

**Comprehension**
`{<key>:<value> for <key_name> in <iteration> if <condition>}`


```python

return {k: [v for v in values if match(k, v)] for k in keys}
```