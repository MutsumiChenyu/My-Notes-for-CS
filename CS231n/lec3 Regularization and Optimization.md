
#### Regulatization (Penlty)

	Loss = Avg(Loss(yi)) + lambda * R(W)

lambda * R(W) --> Regularization: Prevent overtraining

lambda --> new hyperparameter Regularization strength

Simple sample:
	`L2 Regu: R(W) = sum(Wij ** 2)`
	`L1 Regu: R(W) = sum(abs(Wij))`
	`L12 Regu: R(W) = sum(Wij ** 2 + abs(Wij))`
	
Why regularization?
---> Since bigger W means bigger arguments, so a slight change in original data will impact the result hugely. Use regularization to confirm the W is a set of small arguments.

Features：
L2: Tend to spread out the weights arguments

#### Optimization
Find the smallest **Loss**

#### Follow the slope
---> Gradient
We know:
	Loss = sum(Lossi) + Regularization
	Lossi = lossFunction(res)
	res = SoftMax(Wx + b)

1. current W | W + h | gradient dW
2. 

