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
所有用接口名声明的内存块dou'yun'xu

##### Overriding & Overloading
Overriding: 覆写 （MRO in python)
Overloading: 重载 （相同函数签名 不同参数接收）

```java
@Override
```
来提示这个方法是覆写的 对一个未覆写的方法写这个会报错
如果子类没有完全覆写 Java也会编译错误