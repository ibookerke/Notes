[[Activation function]]:
- Adding "non-linearity"to the neural network
- Neural networks without activation functions - just linear regression models

- Most real world data is not linearly separable
- It might become separable in a higher (or sometimes lower) dimensional space
- [[Activation function]]s can help map the data to a different dimensional space
- Non-linear activation function allows the model to learn more complex patterns
- Sparsity / Computation / Feature Hierarchies
- [[Sigmoid]], [[ReLU]], LeakyRelu


# Activation Functions:
### [[Sigmoid]]
#### Features
- Sigmoidal curve ranging from 0 to 1 
- Smooth gradient, differentiable at any point
#### Strengths: 
- Easy to work with analytically
#### Disadvantages: 
- [[Vanishing gradient]] problem, unsuitable for deep networks 
- Outputs are not zero-centered, which can slow down learning
![[Screen Shot 2023-09-27 at 08.08.35.png]]

<hr>

### Rectifeid Linear Unit ([[ReLU]])
#### Features: 
- Output 1 is the input for positive values, zero for negative inputs 
- Output range from 0 to infinity
#### Strengths:
- Computational efficiency
- Sparsity, addresses the vanishing gradient problem
#### Disadvantages:
- Sensitive to outliers and can "die"during training, causing dead neurons that no longer update
![[Screen Shot 2023-09-27 at 08.14.44.png]]

<hr>

### Leaky Rectified Linear Unit ([[Leaky ReLU]])
#### Features:
- Non-linear
- Output range from negative infinity to positive infinity
#### Strengths:
- Computational efficiency
- Addresses the dying [[ReLU]] problem
#### Disadvantages:
- Not zero-centered output
![[Screen Shot 2023-09-27 at 08.20.13.png]]

