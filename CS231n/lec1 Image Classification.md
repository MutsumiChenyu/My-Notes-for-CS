图像--数据矩阵--data tensor
Tensor size -- resolution \* channels
##### Challenges
改变视角会完全改变像素的数据（0-255）但是物体其实还是一样的
光照条件不同

#### Machine Learning
1. Collect dataset
2. Use machine Learning algorithm to train
3. Evaluate the model on new data

#### Nearest Neighbor Classifier
通过记忆原始数据集 对新的测试数据与原始数据进行比对 差距最近被输出label
![[距离计算.png]]
判断两个图像所代表的矩阵的数据差值--也就是两者的距离

**增加可靠性**
1. 使用K-Nearest 
2. 距离计算方式不同 -- L1曼哈顿距离 L2欧氏距离 L...
距离计算方式和特征保留有关
![[L1L2.png]]
L1旋转之后（更换选取的特征值）两点的距离会发生改变
L2旋转之后距离不变
->因此L1可以保留一些必须的信息 L2不能保留这些信息

#### Hyperparameters
1. 选取几个K作为最近邻？
2. 选取L1 还是 L2
这些选择都是超参数设置

![[Pasted image 20260603110216.png]]