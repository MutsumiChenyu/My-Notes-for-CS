
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

