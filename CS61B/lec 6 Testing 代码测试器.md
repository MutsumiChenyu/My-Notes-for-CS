#### 测试器函数编写

```java
public class test{
	@Test
	public void testV{
		double[] input = {10, 20, 30, 40};
		double expected = 125.0;
		double actual = Variance.variance(input);
		/*报错信息库引入 assert语句*/
		assertThat(actual).isEqualto(expected);
	}
}
```