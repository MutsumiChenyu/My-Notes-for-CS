
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
