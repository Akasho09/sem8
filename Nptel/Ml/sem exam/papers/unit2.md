# Matrix Formulation (Normal Equation) 👇
| x₁ | x₂ | y  |
| -- | -- | -- |
| 1  | 3  | 6  |
| 2  | 4  | 8  |
| 3  | 5  | 10 |

1. 🔷 Step 1: Model Form
Multiple Linear Regression:
> y=β0​+β1​x1​+β2​x2​

2. 🔷 Step 2: Matrix Representation
- Design Matrix X
    - col1 = (bias column of 1s)
    - col2 = x1
    - col3 = x2
- X=
  [ ​1 1 3 
    1 2 4
    1 3 5 ]

- Output Vector Y
Y=
[ ​6
  8
  10​ ]
​
3. 🔷 Step 3: Normal Equation
> β=(X^T* X)^−1 X^T*Y
- 
B = [ ​β0
      ​β1​
      β2​​
    ]
​- β0 = intercept
- β1,β2 = feature coefficients.

# linear regression line using Gradient Descent.
1. Step 1: Linear Regression Equation
y^​=mx+b
- Gradient descent update rules:
> m:=m − α*∂J​/∂m
> b:=b − α*∂J​/∂b
- For n samples:
    - ∂J/∂m =​ 2/n*​∑xi​(ŷ​i​−yi​)
    - ∂J/∂b =​ 2/n*​∑​(ŷ​i​−yi​)
- Given:
    - n=3
    - m0=10
    - b0=0
    - Learning rate α=0.1

1. Iteration 1
- Initial:
m=10,b=0
| x | y | (ŷ)      |      (ŷ-y) |
| - | - | -------- | ---------- |
| 2 | 4 | 20       | 16         |
| 3 | 6 | 30       | 24         |
| 5 | 8 | 50       | 42         |

- Compute Gradients
    - ∂J/dm​=2/3​[(2)(16)+(3)(24)+(5)(42)]
similarly dj/db

- Update Parameters
- m1=10−0.1(209.33)
m1=−10.933
- b1=0−0.1(54.67)
b1=−5.467

2. Iteration 2
m=−10.933,b=−5.467

| x | y | (\hat y) | (\hat y-y) |
| - | - | -------- | ---------- |
| 2 | 4 | -27.333  | -31.333    |
| 3 | 6 | -38.266  | -44.266    |
| 5 | 8 | -60.132  | -68.132    |

- same proces and get m1 and b1

- Approximate Regression Line After Two Iterations
- y=24.809x+4.115

# a) Stochastic Gradient Descent (SGD)
- Stochastic Gradient Descent is an `optimization algorithm `used to minimize the `cost function` in machine learning models.
- Unlike Batch Gradient Descent, SGD updates model parameters using one training example at a time.
- Working of SGD
    - For each training sample:
        - Compute prediction.
        - Calculate error.
        - Update weights immediately.
- Weight update rule:
> w:=w−η∇J(w)
- Where:
    w = weight
    η = learning rate
    ∇J(w) = gradient of cost function
- Characteristics
    Faster updates
    `Requires less memory`
    `Suitable for large datasets`
    Noisy but faster convergence
- Advantages
    Efficient for huge datasets
    Faster learning
    Can escape local minima
- Disadvantages
    Oscillates near optimum
    Less stable convergence
- Applications
    Deep Learning
    Neural Networks
    Online Learning Systems

# (b) Softmax Regression
- Softmax Regression is an `extension of Logistic Regression` used for `multi-class` classification problems.
- It predicts probabilities for multiple classes.
- Softmax Function
 >   - P(y=i)=​e^zi​​ /(j=1->k)∑​e^zj 
- Where:
    zi = score for class i
    k = number of classes
- Characteristics
    Output probabilities sum to 1.
    Used when classes are mutually exclusive.
- Example
    - Classifying an image into:
        Cat
        Dog
        Horse
- Advantages
    Handles multiple classes efficiently
    Produces probability outputs
- Disadvantages
    Sensitive to outliers
    Computationally expensive for many classes
- Applications
    Image Classification
    NLP
    Recommendation Systems

# (c) Elastic Net Regression
- Elastic Net Regression combines:
    L1 Regularization (Lasso)
    L2 Regularization (Ridge)
- It helps improve prediction accuracy and feature selection.
- Cost Function
    > J(θ)=RSS+λ1​∑∣θ∣+λ2​∑θ^2
- Where:
    - RSS = Residual Sum of Squares
    - L1 term encourages sparsity
    - L2 term reduces large coefficients
- Characteristics
    Performs feature selection
    Handles multicollinearity
    Prevents overfitting
- Advantages
    Combines benefits of Ridge and Lasso
    Works well with correlated features
- Disadvantages
    More complex tuning
    Requires selecting two regularization parameters
- Applications
    High-dimensional datasets
    Genomics
    Finance prediction systems

# (d) R-Squared vs Adjusted R-Squared
- R-Squared measures how much variance in the dependent variable is explained by the model.
- Formula:
    > R^2 = 1−​SSres​​/SStot
- Range
    - 0≤R^2≤1
- Higher value indicates better fit.
- Limitation of R2
    - Adding more predictors always increases or maintains R2, even if predictors are irrelevant.

2. Adjusted R-Squared
Adjusted R2 modifies R2 by considering the number of predictors.
- Formula:
> Adjusted R2=1−(1−R^2)n−1​/n−p−1 
- Where:
    n = number of observations
    p = number of predictors

| Feature                             | R-Squared         | Adjusted R-Squared  |
| ----------------------------------- | ----------------- | ------------------- |
| Considers number of predictors      | No                | Yes                 |
| Always increases with new variables | Yes               | No                  |
| Reliability                         | Lower             | Higher              |
| Best for                            | Simple regression | Multiple regression |

- Conclusion
    SGD is a fast optimization technique for large datasets.
    Softmax Regression is used for multi-class classification.
    Elastic Net combines Ridge and Lasso regularization.
    Adjusted R2 is more reliable than R2 for multiple regression models.

# (a) Batch Gradient Descent
- Batch Gradient Descent is an optimization algorithm used to minimize the cost function in machine learning models.
- In this method, the entire training dataset is used to compute gradients before updating model parameters.
- Working Steps
    Initialize weights randomly.
    Compute predictions for all training samples.
    Calculate total cost.
    Compute gradients using the whole dataset.
    Update weights.
    Repeat until convergence.
- Weight Update Rule
> w:=w−η*∂J(w)​/∂w
> Stochastic : w:=w−η∇J(w) 
- Where:
    w = weights
    η = learning rate
    J(w) = cost function
- Characteristics
    Uses full dataset for every update
    Stable convergence
    Computationally expensive for large datasets
- Advantages
    Smooth and accurate convergence
    Deterministic results
    Easier to analyze mathematically
- Disadvantages
    Slow for very large datasets
    Requires high memory
    Not suitable for online learning
- Applications
    Small and medium datasets
    Linear Regression
    Logistic Regression

# (b) Micro and Weighted F1-Score
- F1-Score combines Precision and Recall into a single metric.
- Formula:
> F1=2×Precision×Recall / Precision+Recall

1. Micro F1-Score
- Micro F1 computes metrics globally by counting:
    Total True Positives
    Total False Positives
    Total False Negatives
- It treats every sample equally.
- Characteristics
    Suitable for balanced datasets
    Gives more importance to larger classes
- Advantages
    Works well for multi-class classification
    Easy to compute
- Limitation
    Minority classes may get ignored.

2. Weighted F1-Score
- Weighted F1 computes F1-score for each class separately and then averages them according to class support.
- Formula:
> Weighted F1= ∑ ni/N * F1i
- Where: ni = samples in class i
    N = total samples
- Characteristics
    Handles class imbalance better
    Considers class frequencies
- Advantages
    More reliable for imbalanced datasets
    Reflects performance across all classes

| Feature           | Micro F1            | Weighted F1                 |
| ----------------- | ------------------- | --------------------------- |
| Calculation       | Global counts       | Class-wise weighted average |
| Handles imbalance | Less effective      | Better                      |
| Focus             | Overall performance | Performance of each class   |

# (c) Bias-Variance Trade-Off
- The Bias-Variance Trade-Off is a fundamental concept in machine learning that balances:
    Model simplicity
    Model complexity
- to achieve good generalization.

1. Bias
Bias is the error caused by overly simple assumptions in the model.
- High Bias
    - Model is too simple
    - Causes underfitting
- Example:
Using linear regression for highly nonlinear data.

2. Variance
- Variance is the error caused by excessive sensitivity to training data.
- High Variance
    Model learns noise
    Causes overfitting
- Example:
Very deep decision tree memorizing training data.

## Trade-Off
Increasing complexity decreases bias but increases variance.
Decreasing complexity decreases variance but increases bias.
- Goal:
Find an optimal balance.

- Visualization
| Condition     | Bias     | Variance | Result              |
| ------------- | -------- | -------- | ------------------- |
| Underfitting  | High     | Low      | Poor learning       |
| Overfitting   | Low      | High     | Poor generalization |
| Optimal Model | Balanced | Balanced | Good performance    |

- Techniques to Handle Trade-Off
    Cross Validation
    Regularization
    Pruning
    Ensemble Methods
    More training data

# (d) Ridge Regression
- Ridge Regression is a regularization technique used to reduce overfitting in linear regression.
- It adds an L2 penalty term to the cost function.
- Ridge Cost Function
> J(θ)=RSS+λ∑θi^2​
- Where:
RSS = Residual Sum of Squares
λ = regularization parameter

- Characteristics
    Shrinks coefficient values
    Reduces model complexity
    Handles multicollinearity
- Advantages
    Prevents overfitting
    Improves generalization
    Works well with correlated features
- Disadvantages
    Does not perform feature selection
    Choosing λ can be difficult

| Feature             | Linear Regression | Ridge Regression |
| ------------------- | ----------------- | ---------------- |
| Regularization      | No                | Yes              |
| Overfitting Control | Weak              | Strong           |
| Coefficient Size    | Large possible    | Shrunk           |
| Feature Selection   | No                | No               |

# Conclusion
Batch Gradient Descent uses the full dataset for parameter updates.
Micro and Weighted F1-scores evaluate classification performance differently.
Bias-Variance Trade-Off helps balance underfitting and overfitting.
Ridge Regression improves model generalization using L2 regularization.

