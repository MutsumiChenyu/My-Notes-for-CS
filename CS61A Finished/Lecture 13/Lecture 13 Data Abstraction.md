
复合值->一个单元进行操作

Using data -> Present data 展示数据
          |-->manipulate data 操作数据

#### Rational Numbers
Def：
numer/ denom
![[Pasted image 20260124152014.png||300]]
**这里的x就是复合数据类型**
![[Pasted image 20260124152102.png]]
Constructor:构建函数 来创造这个复合数据类型
Selector: 选择器 来选择出这个复合数据类型的原有组成部分

#### Abstraction Barriers 抽象屏障
事实上就是程序的**模块化** 修改程序只需要修改一部分内容

![[Pasted image 20260124152759.png]]
理解一下这三层：
第一层 也是最高层 是Application层 这里通过中层调用 已经实现了把有理数堪称一个完整的数据 来编写高阶程序和业务逻辑
第二层 中层 这一层完成最基础的函数编写 Constructor & Selector来给上面的应用层调用 同时完成了对有理数部分的分析
第三层 底层 这一层用最底层的List等数据结构储存索引


简而言之：比如3/8和1/10
第一层： `[3, 8], [1, 10]
第二层： numer：3， 1 ; denom: 8, 10
第三层： 实现这两个数据的加和或者乘除

存储--取用--运算 三层逻辑架构实现

下面还有更低的层次 实现List这些数据结构 一直往下到001100011

不使用构造函数就会相当复杂 写的很乱 没有 Code Quality

#### Pairs
##### List
>>>`pair = [1, 2]`
>>>`x, y = pair`

**Unpacking:**
选择运算符 []
赋值方法`x, y = pair`
内置函数 `getitem(pair, 0)`


找到最简因数：
```python
from fractions import gcd
#gcd是找到两个数的最大公因数
def rational(n, d):
	g = gcd(n, d)
	return rational[n // g, d // g]
```