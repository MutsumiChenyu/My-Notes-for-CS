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

