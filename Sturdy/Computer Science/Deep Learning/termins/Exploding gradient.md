**If the gradients are large, the multiplication of these gradients will become huge over time**. This results in the model being unable to learn and its behavior becomes unstable. This problem is called the exploding gradient problem.

![[Screen Shot 2023-09-27 at 04.54.43.png]]

- sample a 4x4 matrix from a gaussian distribution
- multiply with another sampled 4x4 matrix, sampled the same way
- repeat 100 times
- matrix product explode

solutions are: batch normalization, less number of layers, careful weight initialization, gradient clipping