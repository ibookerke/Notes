1. **[[Objective function]] (Cost Function)**:
    - **Purpose**: The objective function is a more general term used to describe the function that a machine learning algorithm aims to optimize during training. It quantifies how well the model is performing and is associated with the overall goal of the machine learning task, such as minimizing error or maximizing a reward.
        
    - **Optimization Goal**: In most cases, the goal is to minimize the value of the objective function. For example, in supervised learning, you typically want to minimize the error or loss to make your model's predictions as accurate as possible.
        
    - **Example**: In linear regression, the objective function is often the Mean Squared Error (MSE), which measures the average squared difference between the predicted values and the actual target values. The goal is to minimize the MSE.
        
2. **[[Loss Function]]**:
    - **Purpose**: The loss function is a specific type of objective function used in machine learning, particularly in supervised learning tasks. It quantifies the difference between the predicted output of the model and the true target values (labels). It measures how well the model is currently performing on a single data point.
        
    - **Optimization Goal**: The goal is to minimize the loss function. Minimizing the loss encourages the model to make predictions that are closer to the true labels.
        
    - **Example**: In binary classification, the binary cross-entropy loss is commonly used. It quantifies the dissimilarity between the predicted class probabilities and the true class labels.
        
3. **[[Error Function]]**:
    - **Purpose**: The term "error function" is often used interchangeably with the loss function. It also quantifies the discrepancy between predicted and true values. However, some contexts might refer to it as an aggregate measure of error over the entire dataset.
        
    - **Optimization Goal**: Like the loss function, the error function is usually minimized during model training.
        
    - **Example**: In the context of neural networks, the error function might refer to the mean squared error (MSE) computed over the entire training dataset as a measure of the network's performance.
