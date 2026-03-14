```java
public class Dog{
	public int weightinpounds;//实例变量
	public static int age;//类变量
	
	public Dog(int w){
		weightpounds = w;	
	}//创建instance方法
	
	public void makeNoise(){//当这边没有static的时候 他就从类方法变成了实例方法 只能能通过类调用
		if (weightinpounds < 10){
			System.out.printIn("ABCDEF")
		}else if(...){
		...
		}else{
		...
		}
	}
	
}
public class Launcher{
	public static void main(String[] args){
		Dog smalldog;//声明变量small dog
		new Dog(20);//new -- key word -- 创建了一个狗实例但是没有symbol 被自动销毁
		smalldog = new Dog(5);
		Dog hugedog = new Dog(100); //相当于是1, 3句的合集
		smalldog.makenoise();
		hugedog.makenoise();
	}
}
```
Dog写dog方法 launcher启动dog（有主方法）

#### Static & Non-static
static---静态，在类下所有实例共享 不能通过实例来修改
non-static---实例的单独属性， 不共享 （\_\_init\_\_)

#### Debugging
