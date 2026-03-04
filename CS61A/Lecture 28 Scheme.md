继承自Lisp的函数式语言--一切皆表达式
表达式-组合表达

#### 简单语句
```scheme
(quotient 10 2)
> 5
(number? 10)
> #f t
```

#### Special Form
```scheme
(if <谓词> <结果1> <结果2>)
如果谓词True 结果1 否则结果2
(and <1> <2> <3>)
(or ...)
(cond ( (con1) ('AAA)))
	  ()

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

