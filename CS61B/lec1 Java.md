
```java
public class HelloWorld{
	public static void main(String[] args){
		System.out.printIn("Hello World");
		}
}
```
All Code is a Part of  CLASS
```java
public class HelloNumbers{
	public static void main(String[] args){
		int x; //声明x存在之后才能使用 并且要声明类型
		x = 0;
		while (x < 10){
		System.out.printIn(x);
		x += 1;
		}
	}
}
```
Java程序会在运行之前检查所有的类型是否正确--static types
```java

public class Large{
	
	public static larger(int x, int y){
		if (x > y{
			return x;
		}
		else{
			return y;
		}
	}
	
	public static void main(String[] args){
		System.out.printIn(larger(5, 10))
		}
}
```
Java函数必须作为class的一部分进行声明

程序先经过编译器编译 确定所有类型 成为一个class文件 再被解释器解释执行

OOP in Java
```java
public class Car{
	
	String model;
	int wheels; //必须先定义实例变量类型
	
	public Car(String m){
		this.model = m;
		this.wheel = 4;//this == self in python
	}
	
	public void drive(){
		if (this.wheel < 4){
		......
		}
	}//java的每一个函数必须有一个返回值 否则必须声明void来确保无东西返回出来
	
	public int wheels(){
		return this.wheels;
	}
	
	public static void main(String[] args){
	c1 = Car("First");
	c2 = Car("Second")
	c1.drive();
	c1.wheels();
	System.out.printIn(c2.wheels);
	}
}
```
java种类的定义往往不需要写this 直接写model wheels也行