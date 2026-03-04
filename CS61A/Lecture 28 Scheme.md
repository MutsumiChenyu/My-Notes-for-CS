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

