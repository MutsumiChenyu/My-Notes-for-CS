
Necessary coding for Numpy in Assign 1
```python
# 1. 看 shape
X.shape

# 2. 行向量 / 列向量
v[None, :]   # row vector -- 遍历所有列向量
v[:, None]   # column vector -- 遍历所有行向量

# 3. 按行求和 -- 行1 列0
np.sum(X, axis=1)
# 这个输出的结果是一个行向量 其他的维度被合并之后删除了

# 4. 按列求和
np.sum(X, axis=0)
# axis = 0代表列 合并按照列合并 只得到一个列向量其他内容被合并了

#################################################################
#
#  keepdims = True
#  这句代表合并后矩阵维度不变 被合并（原先被删除）的维度所有元素变成1）
#
#################################################################


# 5. 先对原内容进行排序 然后取出排序的数组的元素的在原数组的index 作为新的输出内容
np.argsort(a)

# 6. 统计 label 出现次数
np.bincount(y)

# 7. 找最大值 index
np.argmax(counts)

# 8. 矩阵乘法 -- @
X @ Y.T
```