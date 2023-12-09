Gradient Descent is **an optimization algorithm for finding a local minimum of a differentiable function**. Gradient descent in machine learning is simply used to find the values of a function's parameters (coefficients) that minimize a cost function as far as possible.


Algorithm:
1. Take the derivative of [[Loss function]] for each parameter in it. Or it is also called - take the gradient of the Loss function
2. Pick random values for parameters
3. Plug the parameter values into the derivatives(Gradient)
4. Calculate the step sizes: 
   Step size = slope x learning Rate
5. Calculate the new parameters:
   New parameter(weight) = old Parameter(weight) - step size
6. Go back to step 3 until step size is too small or you reach the maximum number of steps
