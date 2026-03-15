
#### Primitive Types
这些类型是基本类型， 在Java中天然存在
int String boolean char byte short double float (8)
```java
//省略版的代码

ABC a = new ABC(...); //new关键字只返回地址
b = a;
------
int x = 5;
int y;
y = x;
x = 2;
```
前面一个会把ab指向同一个对象 但是后面一段代码会把x y分别创建

 y = x 把x中的所有bits拷贝到y中 这就是为什么下面的int会有两个内存块储存数据
#### Reference Type
除了基本类型， 其他Java类型都是引用类型 包括Array， List......
对于引用类型 创建实例时产生了一个对这个实例的引用

这里的new 为这个对象开辟了一块内存块并且存储了这个对象的信息 然后新的keyword告诉这个对象存储在什么地方

 **`ABC a`**   这段代码并没有存储 ABC这个实例的信息 而是存储了一个指向这个示例的引用信息 