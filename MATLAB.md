#### 矩阵运算 
`A .* B`  逐元素相乘

`A * B` 矩阵乘法

`inv(A)`矩阵求逆

`A'`矩阵转置

**`rand(row, col)生成一个特定大小的随机矩阵，每个元素都在0，1之间（两边都能取到）`**

`size(particularMatrix)`得到一个数组 -- [row, col] of this Matrix

**创建一个特定元素的矩阵**：先创建0矩阵 然后用循环修改元素

Matrix[index] = [] %删除某个index的元素 并且进行平移（只能对Array）

num2srr(content) 把content转化成字符串，并且保留格式
Matrix也可以哦um

#### 逻辑运算
`x = [1, 3, 7, 10];

`x > 2 & x < 8

>>> 	[F, T, T, F]

&& || 就是正常的逻辑运算
& | 为 Bitwisie运算 可以对数组进行**逐元素**比对

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
#### fprintf填充
`fprint("%d th Hello \n", count)`
%d代表整数，%f代表浮点数
#### for
```matlab
for variable = start:increment:stop
1:2:5 = 1, 3, 5
% 包含头尾 increment步长
```
#### try-catch
```matlab
try
	doA
catch % if A failed
	doB
end
```
#### tic-toc
tic--开始计时
toc--结束计时

#### Row-Col储存方式 -- 外层Col
![[Pasted image 20260602104809.png]]

因为Matlab的内存储存方式--每一列的元素在内存中是连续的
因此在外层用Col数来循环节约程序执行时间