
Necessary coding for Numpy in Assign 1
```python
# 1. 看 shape
X.shape

# 2. 行向量 / 列向量
v[None, :]   # row vector
v[:, None]   # column vector

# 3. 按行求和 -- 行1 列0
np.sum(X, axis=1)

# 4. 按列求和
np.sum(X, axis=0)

# 5. 排序后取 index -- 得到的是index的array
np.argsort(a)

# 6. 统计 label 出现次数
np.bincount(y)

# 7. 找最大值 index
np.argmax(counts)

# 8. 矩阵乘法 -- @
X @ Y.T
```