
#### str与repr
```python
half = fraction(1, 2)
str(half)
>>> '1/2'
repr(half)
>>> fraction(1, 2)
```
由此可见：
str是展示这个对象的值 是用户
repr是展示这个对象的表达式 是解释器导向
`eval`是逆向的repr 负责评估表达式 对repr执行eval会返回这个对象本身

#### f-expression
```python
print(f'pi is {pi}')
```
f会让它后面的那个字符串把其中的{ }内部的对象进行评估得到值 最终结合这个值一起print出来
其中的子表达式在当前的frame中被评估

#### Interface与特殊方法
python在底层有一个最大的class--object 包含了所有的大接口比如：
	\_\_ add init str repr bool float\_\_
这些接口被所有对象互通所以不可能调用时报错 但是如果你要实现自己的str内容 还是得自己行医

#### 运算符重载
python使用的是运算符重载 a + b 被翻译成 a.\_\_add\_\_(b)

