Python的容器总是自动提供一个迭代器 来对他自身的元素进行改动
因为比如容器 list map filter dict 他们都是调用一个相同的__next__迭代器接口来实现功能的
**因此 Python使用迭代器能够实现快速转换数据类型 本质是转换了迭代的方式 最终的迭代接口和数据类型不变 从而节约内存**

迭代器的高级优化作用：
1. 解耦了数据的存储 和 数据的调用
2. 实现了流式读取 允许机器不完全加载所有数据而是单条读取 从而大量节省内存降低空间复杂度
#### iter & next
示例
```python
#链表的迭代
s = [3, 4, 5]
t = iter(s)
next(t) = 3
next(t) = 4
next(t) = 5
list(t)#只显示当前可以迭代的东西 已经输入的比如这里的3 不会再被列出来
比如这个时候写一个list(t) 很显然这里就只会显示： []
#超出范围：
>>>StopIteration #来展示超出范围的报错

#字典的迭代--分为keys和values分别迭代
numerals = {'I': 1, 'V': 5, 'X': 10}
t2 = iter(dict.keys())
#t2 就是一个 I V X的迭代



```
本质是一个position
值得注意的是 改变一个已经调用过迭代器的数据 会使这个迭代器停用
比如改变一个字典的keys 会让改变前所有的针对key的迭代器失效
但是如果改变的是values 那么所有的keys迭代器不会产生任何变化 仍然可以调用

#### `for i in iter(dict{...})` 
遍历某个迭代器的写法 仍然是for循环

#### Lazy Functions -- Built-in Functions
指的是 运用迭代器原理的函数 不会预先处理数据 而是在运行函数的时候才逐条读取数据并进行计算
有这些内容：
```python
filter(func, datas)
map(func, datas)
datas.insert(index, new_data)
reversed(data)
zip(data1, data2)
...#还有很多 主要是和数据结构有关的函数
```
这些函数都不会直接读取所有数据 他们调用这个数据结构data的迭代器 然后逐条读取并且进行输出 防止了一下读取大量数据造成栈爆炸

Lazy函数本质上是返回了一个对象 这个对象只是存储了两个东西：原数据+方法 再加上一个迭代器协议
要让他们自己输出 要加上一些**急躁函数** 比如list, sorted, max, min ... 这两个函数会一下子读取完所有的数据内容并作出相应的处理
或者使用for循环强制next遍历走完所有的迭代器 才能完全走完这些lazy函数

或者：
```python
s = [3, 4, 5]
t = iter(s)
print(*t)
```
这里的\* 会让python完全自动触发迭代器



