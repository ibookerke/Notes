Cross-validation is **a resampling method that uses different portions of the data to test and train a model on different iterations**. It is mainly used in settings where the goal is prediction, and one wants to estimate how accurately a predictive model will perform in practice.

Algorithm
• Train model on part of data 
• Test model on other part of data 
• Repeat on different cross-validation folds 
• Average performance on test set across all folds