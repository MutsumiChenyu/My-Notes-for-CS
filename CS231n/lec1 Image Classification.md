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
![[Pasted image 20260603104121.png]]
判断两个图像所代表的矩阵的数据差值--也就是两者的距离