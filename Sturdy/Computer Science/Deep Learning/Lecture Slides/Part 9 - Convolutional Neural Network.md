# DNN overview
DNN - deep Neural Network
DNN description:
- Learnable weights and biases with [[Backpropagation]]
- Each neuron receives some inputs, performs a dot product
- [[Activation function]]s (non-linearity)
- [[Loss function]] (e.g. SVM/Softmax)
- One-dimensional input vectors
- DNN ignores the rich structure of the image (by Flattening)
- Spatial relation between pixels are not considered

Example:
- Assume our DNN has an input layer corresponding to the 28x28 pixels, making it 784 input neurons
- Our DNN has two hidden layers, and 10 output neurons (10 classes)
- First hidden layer : 784 × N1 + N1 (weights + biases)
- Second hidden layer : N1 × N2 + N2 (weights + biases) 
- Output layer : N2 × 10 + 10 (weights + biases) 
- Total parameters : 784 × N1 + N1 + N1 × N2 + N2 + N2 × 10 + 10
- Input layer with 784 neurons, two hidden layers with N1 = 256 and N2 = 256 neurons, and an output layer with 10 neurons.

The total number of parameters is 268,322

## Limitations of DNN
- **Memory Requirement**: Increasing N1 and N2 exponentially increases the total number of parameters, which in turn requires more memory.
- **Computational Complexity**: A larger number of parameters requires more computational power, increasing the time for each epoch during training.
- **[[Overfitting]]**: With a larger parameter space, the model is prone to overfitting, thereby reducing its ability to generalize to new data.
- **Diminishing Returns**: Beyond a certain point, increasing the size of the hidden layers does not yield a proportionate increase in performance.
- **Optimization Challenges**: A larger parameter space can complicate the optimization landscape
- **Hardware Limitations**: Not all hardware can efficiently handle large-scale neural networks.

<hr>

# Convolutional Neural Networks 
[[CNN]]
- Now we will train the weights in convolutional filters
- This will maintain spatial hierarchy of data
- Recognize patterns in localized regions
- Transform the raw pixel data into higher-level features
- Weight sharing / spatial relationships / translation invariance
## [[Filter]] (kernel) on image
- Each filter has a specific purpose
- Dimension of 3x3 filters
- Sharpness, blur, edge detection, ...
## Convolution operation
- Element-wise multiplication
- Output is called a feature map

- Characteristics or features of the given input image will be emphasized by these [[filter]]s.
- Each [[Filter]] is specialized to emphasize different features, such as edges, corners, colors, or textures
![[Screen Shot 2023-09-27 at 06.49.41.png]]

## Key components in Convolutional Neural Network
1. Convolutional Layer ([[Conv Layer]]) 
2. [[Activation Function ]]
3. [[Batch Normalization]] ([[LRN]])
4. [[Pooling Layer]]
5. [[Dropout Layer ]]
6. Fully Connected Layer ([[FC Layer]]) 
7. [[Loss Function ]] ([[Log loss]])
8. Optimization Algorithm

### Important terms:
- [[Stride]]
- [[Padding]]
- [[Hyperparameters]]

### Input and Output sizes
![[Screen Shot 2023-09-27 at 07.18.57.png]]
Preserving image size and Edge Information, Training Stability

Example1:
- input volume = 32 × 32 × 3 
- Filter size = 5 × 5 × 3 [[Filter]] 
- output size = 28 x 28 x 3

Let's say we want the output volume to remain 32 × 32 × 3
To do this, we can apply a zero padding of size 2:
`O = [(32 - 5 + 4)/1] + 1` 
=> O = 32

Example 2:
![[Screen Shot 2023-09-27 at 07.45.33.png]]

