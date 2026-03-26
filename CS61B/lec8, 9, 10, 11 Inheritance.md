继承，子类，接口
#### Hyponymic Relationship

--->List--->SLList, AList List是另外两个数据结构的Hypernym（上义词）

如何在Java中表示：
1. 为最高级的创建一个RType
2. 声明这两个都属于这个最高级的Type

```java
public interface List{
	public void addFirst(Item x);
	public void addLast(Item x);
}
```
我们把已经实现过的方法贴入List里面 删去这个类型特有的方法 保留公共的 然后删去公共方法的实现细节 把元素类型改成Item

#### Interface Heritance
上述内容是Interface 包含了这个基本数据类型必须包含哪些方法的信息
What, not How.
```java
public interface List{
	public void addFirst(Item x);
	public void addLast(Item x);
}
/* How to Use the Interface? */
public class AList<Item> implements List<Item>{
//相当于Subclass in Python

}
```
所有用接口名声明的内存块都允许接受子类的名称

##### Overriding & Overloading
Overriding: 覆写 （MRO in python)
Overloading: 重载 （相同函数签名 不同参数接收）

```java
@Override
```
来提示这个方法是覆写的 对一个未覆写的方法写这个会报错
如果子类没有完全覆写 Java也会编译错误

#### Implementation Inheritance 实现继承
不仅继承所有签名 也继承一部分方法
在List中不实现是因为List的底层数据结构不同 类型方法不通用
```java
public interface List{
	public void addFirst(Item x);
	public void addLast(Item x);
	/* Default keyword allows the implementation Inheritance 实现继承 */
	default public void print(Item x){
		......
	}
}
/* How to Use the Interface? */
public class AList<Item> implements List<Item>{
//相当于Subclass in Python

}
```

如果这个default对某一个子类无效或不好呢？
仍然可以Override

#### Static & Dynamic Type

Static 静态编译时类型
```java
List a;
```
那么这个a就在编译时确定为List类型

Dynamic 运行时类型
```java
a = new AList();
```
这边的AList就是动态类型 检查这个a实际指向一个什么类型
我们将使用动态类型覆写的方法

#### 构建RotatingSLList
这个继承自SLList 新关键词：Extend

extend用于子类和父类  implements用于接口和第一子类
class-class                    interface-class
```java
public class rotatingSLList<Item> extends SLList <Item>{
	//Generic "Item"
}
```
接下来只需要构建关于这个子类的特殊方法就能完成了

#### 构建VengefulSLList
记忆所有被删除的元素并且存放--重写removeLast
仍然支持Override
注意：私有的元素即使是子类也无法访问 --- 关键词super
```java
public VengefulSLList(){
	//注意这边产生了一个Implicit Call, Java会自动优先调用父类的构建函数
	super();//Java will do this automatically
	lostItem = new SLList<>();
}
public VengefulSLList(Item x){
	//如果有一个初始元素，就必须显式调用super 否则只会执行默认的父类构造
	super(x);
	lostItem = new SLList<>();
}
@Override
public T removeLast() {
	T x = super.removeLast();
	lostItem.add(x);
	return x
}
```
super--走到父级并且执行父级的这个方法

#### 最大的父类--Object （Similar to Python)

所有class都继承了object中编写的方法

implements和extend都是 is-a的关系

#### Encapsulation
	Manage Complexity
隐藏实现细节 只提供Interface

#### 编译时类型检测
比如声明了一个SLList 他的动态类型是Vengeful 但是静态是SLList 导致对这个对象调用lostItem时会产生Compile Error
```java
SLList<Integer> s1 = new VengefulList<>(); //Correct
VengefulList<Integer> s2 = new SLList<>(); //Compile Error
```
一定要保证右边的类型高于或者与左边的类型相等
Compiler不关心最终返回了什么 他只是找这个方法定义时写死的返回的值的类型
##### 强制类型转换
```java
VengefulList<Integer> s2 = new SLList<>(); //Compile Error
class2 A = (class2) func1(A, B);
```

#### High Order Functions in Java

在老Java中没有一个函数类型作为参数传入 不允许传入函数参数
->方法： 创建一个类包装这个函数然后传入

```java
public interface IntUnaryFunc{
	public int apply(int x);
}

public class TenX(){
	public int apply(int x){
		return 10 * x;
	}
}
/*---------------------------------------------------------*/

public class HofDemo {
	public static int dotwice(IntUnaryFunc f, int x) {
		f.apply(f.apply(x));
	}
}
```

可以看到的是 必须把函数封装在一个接口下的一个类 才能被传入函数中
同时调用不得不写成方法的模式

新版的Java已经支持了函数参数的特性 具体写法如下
```java
```

#### Subtype Polymorphism 子态多样性
例子：找出一个适用于多种类的最大值函数
写一个接口 让Dog类实现这个接口的功能 从而实现比较Dog而不创建一堆不同的方法

