
#### Primitive Types
这些类型是基本类型， 在Java中天然存在
int
```java
//省略版的代码

ABC a = new ABC(...);
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
除了基本类型， 其他Java类型都是引用类型