Layer that implements [[Dropout]]

The dropout layer is **a layer used in the construction of neural networks to prevent overfitting**. In this process, individual nodes are excluded in various training runs using a probability, as if they were not part of the network architecture at all.

- Regularization technique to reduce [[Overfitting]]
- Random neurons are "dropped out"(deactivated)
- Not contribute to the forward-pass/[[backpropagation]]
- In AlexNet, it applied tofirst two fully connected layers
