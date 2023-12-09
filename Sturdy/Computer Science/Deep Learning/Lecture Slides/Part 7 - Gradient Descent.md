Most Machine Learning algorithms are set up like this:
- Define an objective function (or error function) f (w, x)
- Compute the gradient w.r.t. its parameters w
- Use gradient ascent (or descent) to optimize the parameters
![[Screen Shot 2023-09-26 at 23.30.34.png]]

Can we just throw any function into gradient descent?
yes but:
If f (w) is [[convex function]], this can result in the global optimum
If f (w) is not [[convex function]], this can result in a local optimum
For convergence, step size η is critical

## How Do We Know Whether f (w) Is Convex?
- obvious examples:
	- f (x) = x^2 , f (x) = x^4 , f (x) = e^x , f (x) = −log(x)
- Evaluate the function and check (hard and resource eating)

The most common approach is:
Compute the [[Hessian matrix]] H of your function f (x)
A function is [[convex function]] if its Hessian is positive definite
![[Screen Shot 2023-09-27 at 01.26.29.png]]
So we are considering a function f(x):
- get the [[Hessian matrix]] of f(x)
- check if [[Hessian matrix]] is positive definite
- if Hessian of f(x) is positive definite then f(x) - [[convex function]] 
  -> the [[Gradient descent]] will not stuck at local optimum

# [[Gradient descent]]
Given a function f (w) : R^D → R^1 
Gradient Descent finds optimal parameters by iterative updates
![[Screen Shot 2023-09-26 at 23.30.34.png]]
A central problem is: What is the best η? 
η - [[Learning rate]]

## Gradient Descent Types:
### [[Steepest descent]]
Steepest descent - basically just choosing a fixed step size η([[Learning rate]])

However, fixed sized [[Learning rate]] can cause the following problems:
![[Screen Shot 2023-09-27 at 01.47.39.png]]
### [[Line Search]] 
- Just take the derivative of f(w), do the step in the direction of it and continue zigzagging

## Mostly used gradient Descent types:
There are some types of [[Gradient descent]]
- [[Stochastic Gradient Descent]] (also called online)
- [[Batch Gradient Descent]]
- Mini-batch gradient descent(basically like stochastic but applied on small batches of data)
every iteration during gradient descent is called ==Epoch==

[[Convergence]] - final state of training when further iterations doesn't improve the model

### [[Stochastic Gradient Descent]]
- Setting the step size η([[Learning rate]]) is difficult for SGD
- Gradient is noisy
	- [[Steepest descent]] will probably not converge
	- [[Line Search]] requires more data points
- Two methods for speeding up SGD [[Convergence]]:
	- Averaging ![[Screen Shot 2023-09-27 at 02.34.21.png]]
	 - Decreasing η with number of iterations t![[Screen Shot 2023-09-27 at 02.35.09.png]]

