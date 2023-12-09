Normalization - standartization of the data to a certain format(preprocessing) suitable for training.
Normalization is needed to handle the unnormalized data, since dizbalanced data with sometimes too high values may lead to [[Exploding gradient]]

![[Screen Shot 2023-09-27 at 09.08.11.png]]

batch normalization is **a method used to make training of artificial neural networks faster and more stable through normalization of the layers' inputs by re-centering and re-scaling**
- Normalize the input layer by adjusting and scaling the activations.
- Reduce the internal covariate shift (Generalization).
- Faster Convergence (high learning rate)
- Less Sensitive to Initialization

## Batch Normalization algorithm:
1. For batch normalization we are normalizing output from the activation function 
   `z = (x-m)/S`
2. Multiply the normalized output by arbitrary parameter g:
   `z * g`
3. Add arbitrary parameter, b, to resulting product
   `(z * g) + b`


Where:
m - mean
S - standard deviation
while b and g are trainable parameters
