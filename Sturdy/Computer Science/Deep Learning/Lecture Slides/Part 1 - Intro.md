# The ML approach
AI systems need ability to acquire knowledge by extracting patterns from raw data
The approach of machine learning: It allowed tackling problems requiring knowledge of real world and make decisions that seem subjective
## Types of ML:
### Supervised learning 
have labeled examples of the correct behavior
Given a set of features/label pairs, find a rule that predicts the label associated with a previously unseen input. 
- Prediction 
- Classification (discrete labels), Regression (real values)
#### Types of supervised learning:

- ==Regression==
  The target output is a real number or a whole vector of real numbers. That is, predict a real number associated with a feature vector, that is, predicting continuous ordered variables.
	  Use linear regression to fit a curve to data.
		  The price of a stock in 6 months time. 
		  The temperature at noon tomorrow.

- ==Classification==
  The target output is a class label. That is, predict a discrete value (label) associated with a feature vector. 
	  The simplest case is a choice between 1 and 0. 
	  We can also have multiple alternative labels.

<hr>
### Unsupervised learning
no labeled examples. Instead, looking for interesting patterns in the data. - Unlabeled data is cheap, labeled data can be hard to get: human annotation Given a set of feature vectors (without labels) group them into “natural clusters” (or create labels for groups). 
- Clustering 
- Probability distribution estimation 
- Finding association (in features) 
- Dimension reduction

<hr>
### Semi-supervised learning
- Self-training is a wrapper method for semi-supervised learning. 
- First, a supervised learning algorithm is trained based on the labeled data only. 
- This classifier is then applied to unlabeled data to generate more labeled examples as input for the supervised learning algorithm.

<hr>
### Reinforcement Learning
- Learning system receives a reward signal, tries to learn to maximize the reward signal. Decision making (robots, chess machine, intelligent agents) 
- Example: DeepMind’s system which learned to play Atari games given raw screen as input, plus the score as the reward signal


# Feature Engineering
### Representation of the Real-World Data 
Features: data’s attributes which may be useful in prediction 
### Feature Transformation and Selection
- Select a subset of the features 
- Construct new features, e.g. 
	- Discretization of real value features 
	- Combinations of existing features 
#### Post Processing to Fit the Classifier 
Does not change the nature

## Limitations of ML
- Limited in ability to process natural data in raw form
- PR and ML systems require careful engineering and domain expertise to transform raw data, e.g., pixel values, into a feature vector for a classifier

It is also difficult to design right set of features 

# Deep learning
Deep learning is a representation learning
- Use ML to not only learn mapping from representation to output but representation itself:
  Better results than hand-coded representations
  Allows AI systems to rapidly adapt to new tasks

- Deep Learning methods are Representation Learning Methods:
  Methods allow a machine to be fed with raw data to automatically discover representations needed for detection or classification

<hr>
## Representation with multiple levels
Compose simple but non-linear modules that transform representation at one level (starting with raw input) into a representation at a higher slightly more abstract level

![[Screen Shot 2023-09-26 at 00.04.10.png]]

## Deep learning characteristics
- A type of Machine Learning that improves with experience and data
- Only viable approach to building AI systems in real-world environments
- Obtains its power by a nested hierarchy of concepts
	- each concept defined by relationship to simpler concepts
	- More abstract representations computed in terms of less abstract ones
![[Screen Shot 2023-09-26 at 00.07.03.png]]
