Pooling layers are **used to reduce the dimensions of the [[ feature map]]s**. Thus, it reduces the number of parameters to learn and the amount of computation performed in the network.

- Lower computational complexity
- Prevent [[Overfitting]]
- Max(Fig.)/Average/Min poolings![[Screen Shot 2023-09-27 at 07.32.12.png]]
- Strided Convolution

## Advantages of using Pooling layers:
1. Spatial Downsampling: Pooling layers help reduce the spatial dimensions of the input feature maps. This downsampling is essential because it reduces the number of parameters and computations in the network, making it more computationally efficient.
    
2. Translation Invariance: Pooling layers introduce a degree of translation invariance into the network. This means that even if an object or pattern is slightly shifted within the input image, the same pooled feature will be activated. This property helps the network recognize patterns regardless of their precise location in the input.
    
3. Feature Abstraction: Pooling layers help the network focus on the most important features in the input data while discarding less relevant information. By selecting the maximum or average value within a pool, the pooling layer emphasizes the most distinctive features and suppresses noise.
    
4. Reduced Sensitivity to Local Variations: Pooling layers make the network less sensitive to small local variations or perturbations in the input data. This property helps improve the model's generalization ability by preventing overfitting to noise in the training data.
    
5. Parameter Reduction: Pooling reduces the number of parameters in the network, which can help prevent overfitting, reduce memory requirements, and speed up training and inference.