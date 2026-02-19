
**函数调用的具体过程**
 ``` python 
 def <name>(<argument>):#Function Signature 
	return <expression>
 ```
  1.添加local frame， 形成一个新环境 称为frame 帧栈
  2.把 函数签名中的形式参数formal parameter bind 到 调用函数时 传入的参数上
  3.执行这个函数本身 call the function

  函数签名function signature包含了创建local frame时所需要的所有参数

**Looking up names in environments**
 An environments is a sequence of frames.
 
 A name evaluates to the value bound to that name in the earliest frame of the current environment in which that name is found.
 任何一个参数 都会向上寻找到他第一次出现的地方（也就是最下面的地方）--environment中的frame 然后把他的值绑定到这个出现的值上

**Environment Diagrams**
 Boxes and arrows 
 Code: Statements and expressions
 Frame: Each name ---> Value, cannot be repeated(name)
 Example: 
 ```Python
 from math import pi
 ```
 这句话实现了一个创建 Global Frame
 同时在这个frame里面 有一个name pi 绑定到值 3.1415926...上

**Print and None**
 ```python
 print(None)
 #output: 
 
 print(abcd)
 #output:abcd
 
 print(None, None)
 #output:None None
 
 print(print(1),print(2))
 ##output:1 2 None None
 ```
  Pure Function--Just return values
  比如 abs（绝对值函数） 和 pow（幂函数power）
  他们接受一个输入值 同时只返回一个输出值 没有其他的副作用
  
  Non-pure Function--Have side effects
  比如print 他接受一个参数
  1.print自带的输出 会输出一个None
  2.print本身的作用 会打印传进去的参数
  ```python
  def print(....):
	  ...
	  return None
  ```
  回头看刚才的print
  ```python
	print(print(1),print(2))
    ##output:1 2 None None
    ```
 执行逻辑如下：
 我要执行外部的大print 就要先解析传进来的参数
 解析参数需要解析print(1) print(2)
 在调用这两个函数的过程中 会自动print出来了1，2
 然后 这两个函数的返回值是 None, None
 这个None，None再被外层的大print打印出来
 最终实现了：
 1
 2
 None
 None    这样的输出
  