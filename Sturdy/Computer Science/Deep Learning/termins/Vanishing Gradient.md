Vanishing gradient problem is a phenomenon that occurs during the training of deep neural networks, where the gradients that are used to update the network become extremely small or "vanish" as they are backpropogated([[Backpropagation]]) from the output layers to the earlier layers.

![[Screen Shot 2023-09-27 at 04.52.59.png]]

- early neural networks often used [[Sigmoid]]s as the [[Activation function]], since they were inspired by biological networks
- when inputs are very large or very small, the sigmoid’s gradient vanishes
- many layers: gradient will go to zero: vanishing gradient problem


Solution?
--[[ReLU]] - now a default choice
