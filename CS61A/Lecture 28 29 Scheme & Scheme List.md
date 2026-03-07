继承自Lisp的函数式语言--一切皆表达式 一切皆函数 一切皆递归
表达式-组合表达

#### 简单语句
```scheme
(quotient 10 2)
> 5
(number? 10)
> #f t
```

#### Special Form
**if or and cond begin let define lambda**
```scheme
(if <谓词> <结果1> <结果2>)
如果谓词True 结果1 否则结果2

(and <1> <2> <3>)

(or ...)

(cond ((con1) ('AAA))
	  ((con2) ('BBB))
	  (else ('CCC)) )
cond的作用相当于if-elif-else

通常来说 一个expression不能写进去两个操作
(begin (print '1) (print '2))
Use begin to operate two expressions at a time

let可以让参数被暂时绑定到某一个名称上 在函数结束调用后自动销毁
(define c (let ((a 3)))
			   (b (+ 2 2)))
		   (sqrt (+ (* a a) (* b b)))))

——————————————————————————

(define <symbol> <expression>) 把某个名称绑定到某个表达式上面
(define (<symbol> <parameter>) <expression>)
(lambda (<parameter>) <body>)
```
define定义的内容称为Procedure 效果等同于函数

#### 用递归定义一个sqrt
```scheme
(define sqrt x)
  (define (update guess))
    (if (= (square x) x))
      guess
      (update (average (guess (/ x guess))))
  (update 1))
```

#### Scheme的列表实现
Scheme的列表是一个本质链表 最后一项指向空集合`nil`
```scheme
(cons first rest) ;;将一个数据和一个列表组合在一起
(car lst) ;;寻找这个列表的头元素
(cdr lst) ;;返回这个列表的剩余部分

nil ;;Scheme's null list
```
所有有关Scheme的列表处理必须使用递归

#### Scheme的引用
```scheme
(a 3)
(b 2)
>(list a b)
>>>(3 2)
>(list 'a b)
>>>(a 2)
```
在Scheme中 ' 表示引用这个符号本身（不是字符串！！！）最终被添加在列表里的不是3 而是符号 a

比如：
```scheme
(car (1 2))
;;Error!
(car '(1 2))
> 1
```
如果没有引用符号 （）里的东西会被评估为一个函数并且执行 所以会报错
当你使用了‘引用符号 那么就代表后面的东西需要被视为一个整体一起评估 才会正确处理这个列表