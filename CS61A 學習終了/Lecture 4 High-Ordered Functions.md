高阶函数

**Local Defined Function**
一个返回函数的函数
```python
def make_repeater(f, n):
    def repeat(x):
        result = x
        for i in range(n):
            result = f(result)
        return result
    return repeat
```
这被称为函数的**Currying**化
func(m)(n)
1.先执行func(m)
2.判断 如果func(m)返回了一个函数 那么这里就满足Currying化的要求
3.用第二个参数n 调用那个返回出来的函数

**lambda 函数定义法**
lambda 匿名函数 写法：lambda x: x * x 不用重新def 可以直接写在里面
区别  lambda x: x * 2  &  x * 2
一个是一个执行的规则（函数） 另一个是一个运算的结果


