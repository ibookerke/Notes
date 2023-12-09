In ML we try to discover patterns: this is fundamental goal of ML/DL
How can we decide whether our model discovered a general pattern or simply memorized the data?
Estimating [[Generalization error]]
![[Screen Shot 2023-09-26 at 00.20.53.png]]

![[Screen Shot 2023-09-26 at 00.23.09.png]]
Left graph is an example of underfitting
Right graph is an example if overfitting

<hr>
# [[Overfitting]] and [[Underfitting]]
Using a larger (more complex) function class allows a better fit with the training data... 

However, despite a low training error, the selected function might not describe the regularity in the data well. It may also be overfitted to the noise that is present in the particular set of samples that is available as training data. 

This overfitting becomes apparent in a [[cross-validation]] when the error on the training data deviates substantially from the error on the test data.

![[Screen Shot 2023-09-26 at 00.32.24.png]]

- high bias: erroneous assumptions. Algorithm misses relevant relations between features and target outputs ([[Underfitting]]) 
- high variance: error from sensitivity to small fluctuations in the training set. Model the random noise in the training data ([[Overfitting]])

![[Screen Shot 2023-09-26 at 00.33.05.png]]

# How to achieve good generalization?
When using powerful algorithms (MLPs, KRR, . . .) every data set can be modeled perfectly! 
([[Overfitting]])
But we want to model new data well (generalization)

[[Cross-validation]] implements this idea:
• Train model on part of data 
• Test model on other part of data 
• Repeat on different cross-validation folds 
• Average performance on test set across all folds

[[Cross-validation]] can be used for:
- Model evaluation 
	- Test how good an algorithm actually is
	-  Report mean evaluation score – e.g. accuracy – across folds
- Model selection 
	- Optimize parameters of a model for generalization performance
	- Take that parameter with the highest mean score across folds

Combined model evaluation and model selection -> Nested Cross-Validation
![[Screen Shot 2023-09-26 at 00.42.45.png]]


![[Screen Shot 2023-09-26 at 00.44.25.png]]
