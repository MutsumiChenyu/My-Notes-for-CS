
#### Regulatization (Penlty)

	Loss = Avg(Loss(yi)) + lambda * R(W)

lambda * R(W) --> Regularization: Prevent overtraining

lambda --> new hyperparameter Regularization strength

Simple sample:
	`L2 Regu: R(W) = sum(Wij ** 2)`
	`L1 Regu: R(W) = sum(abs(Wij))`
	`L1-2 Regu: R(W) = sum(Wij ** 2 + abs(Wij))`
	
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
2. **gradW(Loss)**
Grad Check -- limit h check method

#### Gradient Descent

Stop based on 1. Loop counts, 2. Enough small loss_value
Basically:
**Grad_Weight = Evaluate(Loss_Function, Data, Weight)**
	Calculate the gradient on the loss function
**Weight -= stepSize \* Grad_Weight**

Step Size == Learning Rate
Reduce the learning rate after a few fixed steps
 
##### SGD Stochastic(随机)
Use **miniBatch**
Batch ---> MiniBatch(32/64/128) ---> Use MiniBatch to handle the GD procedure

Random batch --> Cover all the data --> Call the procedure "An Epoch"

Hyperparameter: Epoch / Batch_size

Problem: Grad = 0, e.g. local minima or saddle

##### SGD + Momentum
Status updating will refer to the previous condition.
In order to avoid the Poor conditioning and grad == 0

	v(t + 1) = Rho * v(t) + grad(f)
	x(t + 1) = x(t) - learning_rate * v(t + 1)

##### Adam








