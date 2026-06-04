
Image -- f(x, W) -- outPut -- 注意匹配向量的维度
W: Parameters; x: Images
![[Pasted image 20260604144458.png]]
原始图像（2\*2） 被竖直展平变成了一个列向量 然后
F = Wx + b 一个线性函数对图像的向量进行线性变换

##### f = Wx + b
W是一系列参数用于进行线性变换
b - Bias Item
输出结果与b 是一个树脂length = 标签数量的向量 -- 用于权衡理哪一个标签“最近”

#### Loss Function & Optimization
衡量模型做的多不好 -- 来选择W和b
优化过程来找到最优的W来让Loss Func实现的最好

![[Pasted image 20260604145303.png]]
Loss = 每个样本的误差平均

#### SoftMax Classifier

把F函数输出的内容转化成概率分布 -- 衡量做的好/不好
![[Pasted image 20260604150128.png]]
把输出的结果标化了 -- 每个xi--每个s --对应一个概率分布

##### 如何衡量结果 -- KL Divergence

D(KL)(P || Q) = sum(P(y)\* log(P/Q))

![[Pasted image 20260604150657.png]]

右边的Correct -- One-Hot编码的正确结果 --正确 = 1， 错误 = 0
左边的概率分布 -- 线性函数f计算的结果进行Softmax概率分布归化
Li -- 损失函数
D（KL）-- KL散度 衡量正确结果与输出的概率分布的离散程度
Loss -- 此处为 Cross Entropy Loss 交叉熵损失

**注意点 y是类别 X是输出的概率， 交叉熵损失函数衡量的是对于正确类别， Loss的大小 -- 概率越高 Loss越小**

CEL：-y\* log(x) -- x Possibility, y Onehot Code

