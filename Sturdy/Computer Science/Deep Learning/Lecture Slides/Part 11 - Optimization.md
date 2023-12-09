
The objective of **Optimization** is to minimize a [[loss function]], which represents the difference between the predicted output and the actual labels.

1. Efficiency: Efficient optimization algorithms can significantly reduce training time
2. Generalization: Better optimization strategies help in generalizing the model to unseen data
3. Stability: Robust optimization algorithms help the model converge to a minimum
4. Scalability: As data sizes and model architectures grow, scalable optimization methods become crucial

# Optimizations
### [[Stochastic Gradient Descent]] (SGD)
#### Strengths:
- Simple and easy to implement.
- Computationally efficient.
#### Disadvantages:
- Can oscillate and miss the optimal solution.
- Sensitive to learning rate.
![[Screen Shot 2023-09-27 at 08.43.55.png]]

<hr>

### Momentum
#### Strengths:
- Accelerates convergence
- Reduces oscillation
#### Disadvantages:
Introduces an additional hyperparameter:
![[Screen Shot 2023-09-27 at 08.45.02.png]]

<hr>

### AdaGrad (Adaptive Gradient Algorithm)
#### Strengths:
- Adaptively scales the learning rate for each parameter.
- Well-suited for dealing with sparse data
  sparse  data - when almost all of the data is 0 and useless
#### Disadvantages:
- The learning rate may decrease too aggressively, making the algorithm converge prematurely.
![[Screen Shot 2023-09-27 at 08.46.04.png]]

<hr>

### Root Mean Square Propagation (RMSProp)
#### Strengths:
- Adapts learning rates during training
- Efficiently trains deep neural networks
- Works well in online and non-stationary settings
#### Disadvantages:
- Requires manual setting of hyperparameters.
- Can be sensitive to the choice of initial learning rate.
![[Screen Shot 2023-09-27 at 08.47.14.png]]

<hr>

### Adam (Adaptive Moment Estimation)
#### Strengths:
- Combines benefits of both AdaGrad and Momentum.
- Less sensitive to hyperparameters.
#### Disadvantages:
- Complexity increases with more hyperparameters.
![[Screen Shot 2023-09-27 at 08.48.14.png]]
[[SoftMax]]