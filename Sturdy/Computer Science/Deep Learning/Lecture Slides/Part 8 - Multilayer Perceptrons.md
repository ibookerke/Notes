- Machine Learning: Algorithms that learn from data
- This idea was inspired by learning in biological brains 
- [[Perceptron]] was a first artificial neural network model 
- But the [[Perceptron]] suffers from severe limitations 
- Multilayer perceptrons made neural networks popular again 
- Essential innovation: Error [[Backpropagation]]

![[Screen Shot 2023-09-27 at 03.08.38.png]]
However there is a problem with [[Perceptron]]s 

Perceptrons cannot separate linearly non-separable data:
![[Screen Shot 2023-09-27 at 03.16.44.png]]

![[Screen Shot 2023-09-27 at 03.25.51.png]]

# [[Activation Function]]
- decide whether a neuron should be activated or no
- differentiable operators for transforming input signals to outputs
- most of them add nonlinearity
- activation functions are fundamental to deep learning
- most common ones are: [[ReLU]], [[Sigmoid]] and [[Tanh]] 
- there is still active research in activation functions

# Most common activation functions
- [[ReLU]]
- [[Sigmoid]]
- [[Tanh]]
- [[Logistic activation function]]
- [[Softplus]]

![[Pasted image 20230927034253.png]]

# Universal Approximation Theorem
A Multi Layer Perceptron with one hidden layer and a finite number of hidden units can approximate any function, However learning that function is the hard part.

# Training Multi Layer Perceptrons:

//add the explanation from statquest

![[Screen Shot 2023-09-27 at 04.30.49.png]]
## Error [[Backpropagation]]
The most important concept that is used for mutlilayer perceptron training:

![[Screen Shot 2023-09-27 at 04.34.24.png]]

![[Screen Shot 2023-09-27 at 04.36.53.png]]

### Example:
![[Screen Shot 2023-09-27 at 04.40.07.png]]
![[Screen Shot 2023-09-27 at 04.40.28.png]]
![[Screen Shot 2023-09-27 at 04.40.41.png]]

### Algorithm:
![[Screen Shot 2023-09-27 at 04.40.53.png]]
# Implementing Neural Networks:
- Neural Networks can be implemented in Object Oriented fashion
- Easy to implement
- Clean modular code structure
- Each layer is an object that implements three functions
	- **Forward**: Compute the output of a given layer
	- **Backward**: Compute gradient of a layers’ output w.r.t module input and its weights
	- **Update**: Change layer weights according to gradient and learning rate

## Numerical Stability and Initialization
- weight initialization is important for numerical stability
- there is also link between the choice of [[Activation function]] and weight initialization
- their combination can play an important role how quickly our algorithm converges
- bad choices can also lead to exploding or vanishing gradients

# [[Vanishing gradient]] and [[Exploding gradient]]
![[Screen Shot 2023-09-27 at 04.50.14.png]]

