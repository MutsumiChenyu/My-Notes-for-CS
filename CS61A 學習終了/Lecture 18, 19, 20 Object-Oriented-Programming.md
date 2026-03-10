
#### class
class-instance-method 类，实例和方法
创建一个class_name的实例：
```python
s = class_name(arguments)
```
class的定义:
```python
class Account:#声明 我要开始定义一个类 Account
	
	#__init__ 初始化方法 让类识别到创建实例时的参数
	def __init__(self, account_holder):
		#称为Attributes
		self.balance = 0
		self.holder = account_holder
		
	#Method 方法 在所有这个类的实例下允许调用
	def deposit(self, amount):
		self.balance += amount
	
	#这句话是一个全局声明 在当前程序执行时 所有Account的实例都能共享这个名单
	#程序结束 内存释放 member销毁
	member = []
```
改变attribute的种类是可行的 有这些做法：
```python
a = Account('Fuck')
#Account是没有backup这个attribute的 但是这里可以写 在程序执行周期内可以调用到a的backup
a.backup = [1, 2, 3]
#但是这只针对a这个实例生效 对于同类型的其他实例不适应
```
```python
a = Account('Fuck')
Account.backup = []
#这个就是在这个类下都添加了这个attribute了 依旧是global frame的存在周期 所有实例都可以调用
```

#### Subclasses 子类 与 Inheritance 继承
子类是一种更具体的类，子类继承父类的所有属性同时拥有自己的特殊属性
比如，这里的A是父类，B是子类：
```python
class A:
    def f(self):
        return 1

class B(A):
# class <name>(<base class>):
    pass

b = B()
b.f()              # 1
isinstance(b, A)   # True
issubclass(B, A)   # True
```
##### Attribute查找规则：MRO
MRO for Method Resolution Order 按照这个顺序进行查找
**如果子类没有写__init__那么默认使用父类的init**
实例--子类--父类
##### Override方法覆盖
找到就终止寻找 所以**同名**子类属性定义会覆盖父类属性定义
##### Super向上搜寻
super关键词允许查找属性时向上寻找，不会让子属性覆盖父属性
用法：
```python
class A:
    def f(self):
        return "A"

class B(A):
    def f(self):
        return super().f() + "B"

B().f()   # "AB"
```
可以发现，虽然这里的f在AB中都有提到，但是super关键词允许找到A的这个f
**语法**
`super().func_name(arguments)`

#### 与继承相对--Composition组合

