# (i) Instance-Based Learning and Model-Based Learning
1. Instance-Based Learning
- Instance-based learning is a learning approach in which the model stores training examples and makes predictions using similarities between new and stored instances.
- It is also called lazy learning because generalization happens only when a query is made.
- Characteristics
    - Stores training data directly.
    - No explicit model is built during training.
    - Prediction depends on distance/similarity measures.
    - Training time is low, but prediction time is high.
- Working
    - Store all training instances.
    - When a new input arrives, compare it with stored examples.
    - Find nearest or most similar instances.
    - Predict output based on neighbors.
- Examples
    - k-Nearest Neighbors (KNN)
    - Case-Based Reasoning
- Advantages
    - Simple to implement.
    - Adapts easily to new data.
    - Effective for complex decision boundaries.
- Disadvantages
    - High memory requirement.
    - Slow prediction for large datasets.
    - Sensitive to irrelevant features and noise.

2. Model-Based Learning
- Model-based learning creates a generalized mathematical model from training data and uses it for predictions.
- It is called eager learning because learning occurs during training itself.
- Characteristics
    Learns patterns and relationships from data.
    Builds a compact model.
    Fast prediction after training.
- Working
    Collect and preprocess data.
    Train an algorithm to learn patterns.
    Build a predictive model.
    Use the model for future predictions.
- Examples
    Linear Regression
    Decision Trees
    Neural Networks
    Support Vector Machines
- Advantages
    Faster prediction.
    Requires less memory after training.
    Better scalability for large datasets.
- Disadvantages
    Training may take longer.
    Model may overfit or underfit.
    Needs retraining for new patterns.

| Feature         | Instance-Based Learning   | Model-Based Learning             |
| --------------- | ------------------------- | -------------------------------- |
| Learning Type   | Lazy learning             | Eager learning                   |
| Data Storage    | Stores training instances | Stores learned model             |
| Training Time   | Low                       | High                             |
| Prediction Time | High                      | Low                              |
| Memory Usage    | High                      | Low                              |
| Examples        | KNN                       | Regression, SVM, Neural Networks |

# (i) Effect of Learning Rate Parameter on Cost Function and Weights
- The learning rate (eta η or alpha α) is a hyperparameter that controls how much the model weights are updated during training.
- The weight update rule in gradient descent is:
> w(new)​=w(old)​−η.∂J​/∂w
- Where:
    w = weights
    η = learning rate
    J = cost function
- Effect on Cost Function
1. Very Small Learning Rate
    Cost decreases very slowly.
    Training takes more time.
    May get stuck before reaching optimum.
- Result:
    Slow convergence.
    High training time.

2. Optimal Learning Rate
    Cost decreases smoothly and efficiently.
    Faster convergence toward minimum cost.
- Result:
    Stable and efficient training.

3. Very Large Learning Rate
    Weight updates become too large.
    Cost function may oscillate or diverge instead of decreasing.
- Result:
Training becomes unstable.
Model may never converge.

- Effect on Weights
1. Small Learning Rate
    Small weight updates.
    Gradual learning.

2. Large Learning Rate
    Large jumps in weight values.
    Can overshoot optimal weights.

- Graphical Understanding
Small learning rate → tiny steps toward minimum.
Large learning rate → jumps across minimum.
Proper learning rate → reaches minimum efficiently.

# (ii) Confusion Matrix Metrics
|                | Reality = 1 | Reality = 0 |
| -------------- | ----------- | ----------- |
| Prediction = 1 | 75          | 5           |
| Prediction = 0 | 5           | 15          |

> Accuracy=TP+TN​ / TP+TN+FP+FN
> Precision= TP​/TP+FP
> Recall=TP​/TP+FN 
> F1=2×Precision×Recall​/Precision+Recall 

# Overfitting and Underfitting
1. Overfitting
- Overfitting occurs when a machine learning model learns the training data too well, including noise and unwanted details.
- As a result, the model performs very well on training data but poorly on unseen test data.
- Characteristics
    High training accuracy
    Low testing accuracy
    Poor generalization
    Model becomes too complex
- Example
    - A student memorizes answers instead of understanding concepts and fails in a different exam pattern.
- Causes
    Very complex model
    Small training dataset
    Too many features
    Excessive training

2. Underfitting
- Underfitting occurs when the model is too simple to capture the underlying pattern of data.
- It performs poorly on both training and testing data.
- Characteristics
    Low training accuracy
    Low testing accuracy
    Model fails to learn patterns
- Example
    A student studies only chapter titles and cannot answer exam questions properly.
- Causes
    Very simple model
    Insufficient training
    Too few features
    High bias

| Feature           | Overfitting   | Underfitting |
| ----------------- | ------------- | ------------ |
| Model Complexity  | Too high      | Too low      |
| Training Accuracy | High          | Low          |
| Testing Accuracy  | Low           | Low          |
| Error Type        | High variance | High bias    |
| Generalization    | Poor          | Poor         |

## Techniques to Reduce Overfitting and Underfitting
### Techniques to Reduce Overfitting
1. Regularization
Adds penalty to large weights to simplify the model.
- Common methods:
L1 Regularization (Lasso)
L2 Regularization (Ridge)
- Example formula:
> J(θ)=Loss+λ*(i=1->n)∑​θi^2​

2. Cross Validation
Split data into multiple parts to validate model performance properly.

3. Dropout (for Neural Networks)
Randomly removes neurons during training to prevent memorization.

4. Early Stopping
Stops training before the model starts memorizing noise.

5. Increase Training Data
More data helps the model generalize better.

6. Feature Selection
Remove irrelevant or noisy features.

## Techniques to Reduce Underfitting
1. Increase Model Complexity
Use a more powerful model.

2. Add More Features
Provide better information to the model.

3. Train for More Epochs
Allow the model to learn sufficiently.

4. Reduce Regularization
Too much regularization may oversimplify the model.

# Conclusion
Overfitting means the model memorizes training data and fails to generalize.
Underfitting means the model cannot learn the data pattern properly.
Techniques like regularization, cross-validation, dropout, early stopping, and feature engineering help reduce these problems and improve model performanc

# Q1 (b) Difference Between AI and Machine Learning
1. Artificial Intelligence (AI)
- Artificial Intelligence is a broad field that enables machines to mimic human intelligence and decision-making.

2. Machine Learning (ML)
Machine Learning is a subset of AI that allows systems to learn automatically from data without explicit programming.

| Feature     | Artificial Intelligence          | Machine Learning                       |
| ----------- | -------------------------------- | -------------------------------------- |
| Definition  | Simulation of human intelligence | Learning from data automatically       |
| Scope       | Broad field                      | Subset of AI                           |
| Goal        | Make machines intelligent        | Enable learning from data              |
| Programming | May use rules and logic          | Uses data-driven algorithms            |
| Examples    | Robotics, Expert Systems         | Recommendation systems, spam filtering |

## Types of Machine Learning Techniques
1. Supervised Learning
- The model learns using labeled data.
- Goal
    - Predict output from input data.
- Examples
    Email spam detection
    House price prediction
    Algorithms
    Linear Regression
    Decision Tree
    SVM
    KNN
2. Unsupervised Learning
- The model learns from unlabeled data.
- Goal
- Find hidden patterns or groups.
- Examples
    Customer segmentation
    Market basket analysis
    Algorithms
    K-Means Clustering
    PCA
3. Semi-Supervised Learning
- Uses both labeled and unlabeled data.
- Advantage
    - Useful when labeled data is limited.
- Example
    - Image classification with few labeled images.

4. Reinforcement Learning
An agent learns through rewards and punishments.
- Components
    Agent
    Environment
    Reward
- Examples
    Self-driving cars
    Game playing AI

# Q1 (c) Difference Between Normalization and Standardization
1. Normalization
- Normalization rescales data to a fixed range, usually between 0 and 1.
- Formula
> Xnorm​= X−Xmin​​/Xmax​−Xmin​
- Characteristics
    Values lie between 0 and 1.
    Sensitive to outliers.
- Used In
    Neural Networks
    KNN

2. Standardization
- Standardization transforms data so that it has:
    Mean = 0
    Standard deviation = 1
- Formula
    > Z=X−μ​/σ
    - Where:
        - μ = mean
        - σ = standard deviation

| Feature             | Normalization        | Standardization              |
| ------------------- | -------------------- | ---------------------------- |
| Range               | Usually 0 to 1       | No fixed range               |
| Formula Base        | Min-Max scaling      | Mean and standard deviation  |
| Outlier Sensitivity | High                 | Lower                        |
| Distribution        | Changes distribution | Preserves distribution shape |
| Used In             | KNN, Neural Networks | SVM, Logistic Regression     |

# 
For heart attack risk prediction, the best metric is usually Recall, followed by F1-score.
- “Out of all actual heart attack risk patients, how many were correctly identified?”

