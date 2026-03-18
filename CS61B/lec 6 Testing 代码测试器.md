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
先写测试函数 确保自己考虑了所有的边界情况 然后再写代码跑通所有样例