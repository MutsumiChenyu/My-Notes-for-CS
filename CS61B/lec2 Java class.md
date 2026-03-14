```java
public class Dog{
	public int weightinpounds;
	
	public Dog(int w){
		weightpounds = w;	
	}//创建instance方法
	
	public void makeNoise(){//当这边没有static的时候 他就从类方法变成了实例方法 只能能通过类调用
		if (weightinpounds < 10){
			System.out.printIn("ABCDEF")
		}else if(...){
		
		}else{
		
		}
	}
	
}
public class Launcher{
	A = Dog(100);
	B = Dog(123);
}
```
Dog写dog方法 launcher启动dog（有主方法）