# Linear Classification
![[Screen Shot 2023-09-26 at 14.28.51.png]]
![[Screen Shot 2023-09-26 at 14.33.34.png]]

As ==***w***== we usually mean(in case of ==linear== classification) a combination of slope and a horizontal shift

What is good w?
In order to answer this question wee need an [[Error Function]] that tells us if w is good or not
![[Screen Shot 2023-09-26 at 14.36.14.png]]
![[Screen Shot 2023-09-26 at 14.39.29.png]]
[[Frank Rosenblatt]] termed this loss function [[Perceptron Criterion]].

How to minimize the [[Error Function]]?
![[Screen Shot 2023-09-26 at 15.17.19.png]]
The answer is [[Gradient descent]]
We minimize errors by walking in the direction of the gradient:
![[Screen Shot 2023-09-26 at 15.37.40.png]]

# Artificial Neural Networks

![[Screen Shot 2023-09-26 at 15.48.57.png]]
[[Perceptron]] is a first neural network which consists of single neuron

[[Frank Rosenblatt]] proposed the [[Perceptron]], an artificial neural network for pattern recognition.
Regarding the perceptrons: “ [. . . ] the fundamental laws of organization which are common to all information handling systems, machines and men included, may eventually be understood.”

# The perceptron learning algorithm
Goal - binary classification
![[Screen Shot 2023-09-26 at 20.31.16.png]]
- Table on the left represents the data, where x is a feature and y is a associated label(it is supervised -learning). 
  x - represent features such as height, age, weight etc.
  y - are the binary labels that can either be 1 or 0
- Then in the center of picture we may see 3 input features x_i and the corresponding weight w_i. 
  In The perceptron learning algorithm we just sum all of (x_i x w_i) and add a bias. It is done it Adder. Then we are pasting the result into the [[activation function]](in this example the [[Sigmoid]] is taken) which just binary classifies if the combination of weight w_i,  feature x_i and bias are providing a result that corresponds the y value. 
- If it corresponds - leave it, however if it doesn't corresponds then we take change the value of weight using formula: 
  w_new = w_old + α( y_i - y(hat) )
  where α - learning rate (like in [[Gradient descent]])
  y_i - right value of y
  y hat - wrong value of y
- So by this move we are updating the weight w_i of a certain feature x_i. 

The perceptron tries to find patterns by trying different features like age, height, etc. Check if they are useful for identifying the end result and if are useful than try to put the choose the right coefficient which represents how important is this weight for the end result.

![[Screen Shot 2023-09-26 at 21.05.57.png]]
This equation can be minimized iteratively using stochastic [[Gradient descent]]
which is just [[Gradient descent]] just randomly picking the parts of the data
![[Screen Shot 2023-09-26 at 21.06.56.png]]

The [[Part 4 - Nearest Centroid Classifier]] and perceptron learning algorithm are called ==Discriminative== methods 
-> they discriminate and predict different categories
However, these methods do not provide a measure of uncertainty about these predictions
what if we want a measure of uncertainty about predictions?
![[Screen Shot 2023-09-26 at 21.41.39.png]]

