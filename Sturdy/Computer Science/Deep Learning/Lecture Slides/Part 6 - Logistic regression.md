[[Logistic Regression]] is not for regression - it's for classification
The goal is to model p(y|x) directly 
- Find a function p(y|x) = g(x) that has probabilistic outputs 
- No need for modeling p(x) and p(y, x) 

[[Logistic Regression]]
- For Binary problems y ∈ {−1, +1}: 
  p(y|x) as Bernoulli Distribution (Binomial with n = 1) 
  Example: Tossing a coin

# Bernoulli Distribution
The Bernoulli distribution is a discrete probability distribution
Example:
- A single toss of a coin 
- Probability of heads (success, X = 1) is q 
- Probability of tails (no success, X = 0) is 1 − q
![[Screen Shot 2023-09-26 at 22.44.56.png]]

<hr>

# [[Logistic Regression]] - Binary Classification
The Logistic regression model
- is based on linear combinations w of features in x
$$ z = w^Tx $$
0 < p(y|x) < 1
∑y' p(y'|x) = 1

![[Screen Shot 2023-09-26 at 22.47.40.png]]
For binary case we may simplify the formula:
![[Screen Shot 2023-09-26 at 22.49.48.png]]
So in order to minimize the negative log-likelihood we need take the gradient(derivative) of the probability fucntion
![[Screen Shot 2023-09-26 at 22.52.11.png]]
![[Screen Shot 2023-09-26 at 22.54.35.png]]

Code example of applying logistic regression on a stochastic [[Gradient descent]]:
![[Screen Shot 2023-09-26 at 22.56.08.png]]

# Perceptron and [[Logistic Regression]]
Technically both logistic regression and perceptron is just squishing the data so applying it to linear model
![[Screen Shot 2023-09-26 at 22.59.57.png]]

You could ask, whether these outputs are really probabilities – and if so, of what?
There are 2 answers:

**YES**: 
they are numbers between 0 and 1 and sum to 1. We defined the model to return the probability of a label, so we will get probabilities.

**No**: 
it’s a linear model with a squashing function. The numbers are probabilistic, but their meaning is arbitrary. 

The truth lies somewhere between these two.
“essentially, all models are wrong, but some are useful”

<hr>
# Multiclass logistic regression

![[Screen Shot 2023-09-26 at 23.06.14.png]]

![[Screen Shot 2023-09-26 at 23.07.29.png]]

![[Screen Shot 2023-09-26 at 23.08.03.png]]

## [[Logistic Regression]] characteristics:
Requires only D + 1 parameters
⇒ Very efficient
Does not make assumptions about the underlying distribution
⇒ Can be applied to large range of data
