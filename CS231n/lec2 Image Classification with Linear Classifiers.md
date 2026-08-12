
---
Target -> Give the correct labels to the matched picture
This is Image classification

Challenges: 光源 遮挡 尺寸 环境 "上下文"

#### Data-Driven Approach

Machine Learning on datasets

---

#### First Classifier -- Nearest Neighbor
Image --> Matrix --> Calculate the distance between two images

##### Distance calculate

L1: sum(P(i, j) - Q(i, j))
L2: sqrt(sum(P(i, j)\*\*2 - Q(i, j)\*\*2))

1 3 5 || 2 4 6 --> Sum = (2-1)+(4-3)+(6-5)

Calculate Procedure：
1. Flatten the image -- Calculation is conducted element by element -- Shape does not change the result
2. Memorize the whole train data
3. Compare each testing data with the whole training data (L1, L2)
4. Store the nearest one in the result matrix -- size(numTraining, 1) -- store the **label(value)** of the nearest matched one in the training data

```python
distances = np.sum(np.abs(self.Xtr - X[i, :]), axis = 1)

# axis = 1 --> Calculate the sum in the row
# self.Xtr --> training data (it is a matrix)
# X --> it is the sum of testing data(multiple matrices)
# X[i, :] --> i-th testing sample
```

Image --  3 Channels
Row resolution \* Col resolution \* 3(R-G-B)

##### Hypermeter Choices:
value of k ?
L1 or L2 or Ln ?

##### Cross-Validation
Training - Fold 1, 2, 3, 4, 5
Each fold plays as validation set in each turn of training

---

#### Linear Classifiers

Image --> matrix: x --> f(x, W) --> numbers with class scores

e.g. x: 3072 \* 1(flattened original data) W: 3072 \* 10
f = Wx = 10 3072 \* 3072 1 = 10 \* 1 -- Each block is each score of the matched class

Each row of W --> A corresponding set of arguments of one specific category
Multiplied by the image vector to get the result corresponding to the  specific category

##### Possibility Function (Normalizing)

**SoftMAX**
P(Y = k | X = xi) = \[e^(resK)] / \[sum(e^(resJ))]

	e.g. 
	Y = 1, 2, 3; f = Wx + b --> res: A, B, C
	total = e^A + e^B + e^C 
	P(Y = 1) = e^A / total

##### Loss Function
for the result of SoftMAX, we check the correct label and calculate the softmax result

	e.g. Loss = -log(P(Y = k))

**Cross-Entropy Loss**
Two possibility - P, Q with same size N

	H(P, Q) = -sumN(Pi * log(Qi))

Due to the correct possibility is labeled by One-Hot(Only 1 and 0) Code, so 
`Loss = -log(P-correct)`

**KL Divergence**

`Div(KL) = sumN[Pi * log(Pi / Qi)]`

**Connection**
In One-Hot code, KL-div == Cross Entropy

Normally,
	`H(P, Q) = H(P) + Dkl(P||Q)`
##### W
Formed by optimizing learning 
![[Linear Classifiers.png|200]]
Each Turn:
1. Use W to calculate result
2. Use Possibility Function to Normalize the result
3. Use result and Loss Function to calculate the loss of this turn
4. According to **Learning Rate**, **Loss Result**, **Gradient Descent** to calculate the new W, which will make the Loss smaller


