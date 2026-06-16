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
![[Matlab-先Col后Row.png]]

因为Matlab的内存储存方式--每一列的元素在内存中是连续的
因此在外层用Col数来循环节约程序执行时间

#### function in Matlab

```matlab
function outputArgu = funcName(inputArgu)
	%function body
end
```

#### 内置函数

```matlab
rand(n, m) % 生成n*m的随机数矩阵
randi([m, M], n) % n*n的方阵 其中数字是[m, M]中的随机整数
randperm(n) % 生成从1-n的随机排列
rng(seed, generator) % 根据特定种子来生成随机数
```

#### 数据类型

##### int & uint
intX - X位整数 -- X = 8, 16, 32, ...
uintX - X位无符号整数 (>= 0)

##### struct array
直接用.创建新结构 在新结构命名后加入(i)来生成struct array
```matlab
student.name = "A";
student.gender = "F";
student.grade = 60;
student(2).name = "B";
student(2).gender = "M";
student(2).grade = 70;
```

##### cell array

#### 文件IO

##### importdata
适用于txt csv等表格文件 可以分离文字内容和数字内容

```matlab
A = importdata('fileName', '分隔符', int-跳过的行数);
```

分隔符 -- 
如果数据的记录形式是1,2,3  那么这里的分隔符就是","
如果是1 2 3 那么就是" "

##### fopen & fclose

```matlab
fd = fopen('filename', permission)
% 文件名， 权限类型;
fclose(fd);
```

##### 权限类型
Read only (default): **r**
Open or create new ﬁle for writing only (discard existing): **w**
Append to a ﬁle: **a**
Read and write: **r+**
Read and overwrite: **w+**
Read and append: **a+**

r+ : ABCDEF -- XYZDEF
从文件头部开始擦除等量内容， 并且填入新内容（头部开始）
w+ : ABCDEF -- XYZ
清空文件后再写入

##### Write
```matlab
fprintf(fileID, 'format', variable);
```
格式和printf的格式基本一致
###### format
"%10.2f\n"
10 -- 输出输入内容位宽 -- 10个字符
.2 -- 输出内容保留两位小数
f -- 输出内容为浮点数 -- 默认保留6位小数
g -- 紧凑型浮点数 -- 保留6位有效数字
010 -- 10位宽 不够的地方用0来填充

format对于矩阵是采用按照列的顺序进行应用的 例如一个两列的矩阵都要应用格数符
"%d %.2f \n" -- 第一列是整数 第二列保留两位小数


##### Read
```matlab
fscanf(fileID, 'format');
```
按照format中的格式要求读取内容， 不填写format就是默认全部读取

```matlab
% 按照行读取
fgetl(fileID) %l 不需要行结束的换行符
fgets(fileID) %s 保留换行符
```

##### EOF
