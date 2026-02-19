
高层代码 无需compile
printf ->print || no backslash n || no 分号

```python
import cs50
from cs50 import get_string

answer = get_string("llll")
print( "llll" + answer ) //+代表连接输入内容
or
print( "llll", answer )//会自动在每个参数之间加入space
or
print( f"llll,{answer}" )//{}代表插值 "f"表示后面会进行插值操作(插值声明)

```
bool  float  int  str 4 data types
range list（数组） tuple dict set(集合)

更低性能--更简洁 Balance

**condition**
```python
if x < y: #没有括号 一定要要求标准缩进
	print("aaaa")
elif x > y: #elif == else if
	print("bbbb")
else:
	print("cccc")
	```
**variable**
int i = 0; ----> i = 0 不用再声明
**Loop**
```python
i = 0
while i < 3:
	print("aaaa")
	i += 1
	
for i in [0,1,2]
	print("bbbb")
	
for i in range(3) #返回相应数量的值 
	print("cccc")
	
while True:
	print("dddd")
```
range will **give you a value repeating 1000 times**
[]will give 1000 values at a time

python不会有integer overflow

可以直接写and和or 对于字符串选取可以使用  **""** 和 **' '**

**Object-oriented Programming** --Python 面向对象编程 s.lower()
**Procedural Programming** --C 过程式编程  tolower(s)

数据结构体 内置了函数

docs.python.org 所有内置函数的参考