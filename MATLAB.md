#### 矩阵运算 
`A .* B`  逐元素相乘
`A * B` 矩阵乘法
`inv(A)`矩阵求逆
`A'`矩阵转置
`rand(row, col)生成一个特定大小的随机矩阵
`size(particularMatrix)`得到一个数组 -- [row, col] of this Matrix

#### 逻辑运算
`x = [1, 3, 7, 10];

`x > 2 & x < 8

>>> 	[F, T, T, F]


&& || 就是正常的逻辑运算
& | 为 Bitwisie运算 可以对数组进行逐元素比对

在MATLAB中 不等号是 `~=`
```matlab

str1 = ["Qwen","Gemini"; "ChatGPT","Ilama"];

str2 = ["Gemini"];

str1 == str2; % compare string array with a string scalar

mask = (str1 == str2); %logical index
% 这里的mask是一个逻辑运算的数组结果 如果二者对应位置相等就是1（T）否则就是0（F）

disp(str1(mask)); %extract all elements identiﬁed by the mask
%string(AAA) 根据AAA的结果提取string的元素
```

`"AB"<"Ab" ; %true`

if-else语句不需要分号 Block需要

#### Switch

```matlab
switch variable
	case A
		Block1
	case B
		Block2
	otherwise
		Block3
end
```