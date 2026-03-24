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

#### 最初的父类--Object（Similar t