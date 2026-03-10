#### 报错信息处理 Exception：
raise语句必须要是BaseExpection的子类
Type Recursion Name Key + Error
```python
raise TypeError #主动提出报错 报错class：类型错误 无报错信息

# try statment
try:
	<operation1>
except TypeError as e: #as e可以去掉 不要这个代号
	<operation2>
```
报错信息并不应该终止这个程序 而应该提供报错信息允许继续输入

#### 解释器设计和计算器

完备的语言需要两个设计：Syntax语法 & Semantics 语义

##### Parse 解析
Text --词法解析-->Token --语法组合-->表达式-->机器执行
例如 (+ 1 2) 先被解析成\[ '(', '+', '1', '2', ')']的Token模式 然后再交给语法分析

计算器设计：
calc_eval--解析表达式的各个元素含义 递归调用完全解析
calc_apply--一个类型的表达式 意义上在eval递归调用的过程中对某一个表达式进行计算得出结果
