#  Logistic Regression Using Gradient Descent
- Logistic Regression is a supervised machine learning algorithm used for classification problems, especially binary classification.
- Examples:
    Spam / Not Spam
    Disease / No Disease
    Pass / Fail
- Unlike linear regression, logistic regression predicts probabilities between 0 and 1.

## Logistic Regression Model
- The hypothesis function is:
> hθ(x)= 1/1+e^−z
- Where:
- z=θ0+θ1x1+θ2x2+⋯+θnxn
- This is called the Sigmoid Function.
- Why Sigmoid Function?
The sigmoid function converts any real value into a probability range:
> 0≤hθ​(x)≤1
- Decision Rule
    If probability ≥0.5 → Class 1
    Else → Class 0

### Cost Function in Logistic Regression
- Mean Squared Error is not suitable because logistic regression is nonlinear.
- Instead, we use Log Loss / Cross Entropy Loss.
- Cost Function:
> J(θ)=−1/m(i=1->m)∑[y^(i)log(hθ(x^(i)))+(1−y^(i))log(1−hθ(x^(i)))]
- Where:
    - m = number of training examples
    - y = actual output
    - hθ(x) = predicted probability

## Gradient Descent in Logistic Regression
- Gradient Descent is used to minimize the cost function by updating weights iteratively.
- Parameter Update Rule
- For each parameter:
> θj​:=θj​−α*​∂J(θ)​/∂θj
- Where:
    - α = learning rate
- Gradient for logistic regression:
> ​∂J/​∂θj ​=1/m(i=1->m)​∑​(hθ​(x^(i))−y^(i))xj^(i)​

## Steps to Solve Logistic Regression Using Gradient Descent
1. Step 1: Initialize Parameters
- Initialize:
    Weights θ
    Bias/intercept
    Learning rate
- Example:
    θ0=0,θ1=0

2. Step 2: Compute Linear Combination
For every training sample:
- z=θ0+θ1x

3. Step 3: Apply Sigmoid Function
hθ(x)=1/1+e^−z
- This gives predicted probability.

4. Step 4: Compute Cost Function
Calculate total error using log-loss.

5. Step 5: Compute Gradients
Find derivatives with respect to parameters.

6. Step 6: Update Parameters
Update weights using gradient descent rule.

7. Step 7: Repeat Iteratively
- Continue until:
    Cost converges
    Maximum iterations reached

# Adaptive Linear Neuron (ADALINE)
- We need to derive weights and threshold using the ADALINE learning rule.
- Given:
    - Initial weights: w1=w2=0.1
    - Bias: b=0.1
    - Learning rate: α=0.1
    - Show only one epoch
- Training Data
| (x_1) | (x_2) | Target (t) |
| ----- | ----- | ---------- |
| -1    | -1    | -1         |
| -1    | 1     | 1          |
| 1     | -1    | 1          |
| 1     | 1     | 1          |

- ADALINE Learning Rule
- Output:
    > yin​=b+w1​x1​+w2​x2​
- Weight update:
    > wi​(new)=wi​(old)+α(t−yin​)xi​
- Bias update:
> b(new)=b(old)+α(t−yin​)

- Initial Values
w1​=0.1,w2​=0.1,b=0.1

1. Epoch 1
Pattern 1
- Input:
    x1​=−1,x2​=−1,t=−1
- Compute Net Input
    yin​=0.1+0.1(−1)+0.1(−1)=-1
- Error
    > e=t−yin​
    =−0.9
- Update Weights
- Update w1 
    - w1=0.1+0.1(−0.9)(−1)
    =0.1+0.09
    =0.19
- Update w2
    w2=0.1+0.1(−0.9)(−1)
    =0.19
- Update Bias
    b=0.1+0.1(−0.9)
    =0.01
- Updated Parameters
    - w1=0.19,w2=0.19,b=0.01

2. Similarly for Pattern 2

3. Similarly for Pattern 3

4. Similarly for Pattern 4

- Final Weights and Bias After One Epoch
    w1=0.24011
    w2=0.22031
    b=0.25811
	​

# Hebb Rule Classification Problem
- Using the Hebbian Learning Rule, find the weights for classification.

1. Step 1: Represent Patterns in Bipolar Form
- Given:
    “+” → +1
    Empty box → −1
- Target:
    Pattern “I” → t=1
    Pattern “O” → t=−1

- Pattern 1 : “I”
Matrix:
[   + + + 
    - + -
    ​+ + + ]

- Convert into bipolar vector (row-wise):
x^(1)= [  1
          1
          1
          -1
          1
          -1
          1
          1
          1 ]
- ​Target:
t^(1)=1

- Pattern 2 : “O”
Matrix:
[   + + + 
    + - +
    ​+ + + ]
- Vector form:
x^(2)= [  1
          1
          1
          1
          -1
          1
          1
          1
          1 ]
- Target:
t^(2)=-1

2. Step 2: Hebb Learning Rule
- Weight update rule:
> w=∑xi.ti
- Initial weights assumed zero.

3. Step 3: Compute Weight Contribution
- For Pattern “I”
Since t=1:
- w(1)=x(1)
     = [  1
          1
          1
          -1
          1
          -1
          1
          1
          1 ]

- For Pattern “O”
Since t=−1:
- w(2)=−x(2)
       [  1
          1
          1
          1
          -1
          1
          1
          1
          1 ]
4. Step 4: Final Weight Vector
> w=w(1)+w(2)
        [0
         0
         0
         -2
         2
         -2
         0
         0
         0]
- Final Weight Matrix Form
Reshape into 3×3:
        [0  0  0
         -2 2 -2
         0  0  0]

- convert to vectors and add.

# Logistic Regression Using Perceptron Model
- The Perceptron Model is one of the earliest neural network models used for binary classification.
- Logistic Regression and Perceptron are closely related because both:
    - Use weighted sums of inputs
    - Perform binary classification
    - Learn decision boundaries
- The main difference is:
    Perceptron uses a hard threshold activation.
    Logistic Regression uses a sigmoid activation and probability output.

- Perceptron Model
    - A perceptron computes:
> z=w0​+w1​x1​+w2​x2​+⋯+wn​xn​
- Where:
    xi = input features
    wi = weights
    w0 = bias
- Activation Function
    In logistic regression, sigmoid activation is used instead of step activation.
- Sigmoid function:
    > σ(z)=1/1+e^−z
- Output range:
    > 0≤σ(z)≤1
- This output represents probability.
- Decision Rule
    If σ(z)≥0.5 → Class 1
    Else → Class 0
- Architecture of Logistic Perceptron
```yml
x1 ----\
x2 ----- > Weighted Sum → Sigmoid → Output
x3 ----/
```
- Logistic Regression Equation
The hypothesis function is:
> hθ​(x)=1​/1+e^(−θT.x)
- Where
θTx=θ0​+θ1​x1​+⋯+θn​xn​

- Training Using Gradient Descent
Weights are updated iteratively to minimize classification error.

- Cost Function
Logistic Regression uses Cross-Entropy Loss:
> J(θ)=−m1​∑i=1m​[y(i)log(hθ​(x(i)))+(1−y(i))log(1−hθ​(x(i)))]
- Where:
m = number of training samples
y = actual label

- Weight Update Rule
Gradient descent update:
> θj​:=θj​−α.1/m​∑i=1m​(hθ​(x(i))−y(i))xj(i)​
- Where:
α = learning rate

## Steps to Solve Logistic Regression Using Perceptron

1. Step 1: Initialize Weights
- Initialize:
    Weights
    Bias
    Learning rate
- Example:
w0=w1=0

2. Step 2: Compute Weighted Sum
z=w0+w1x

3. Step 3: Apply Sigmoid Function
> y^=σ(z)
- Obtain probability output.

4. Step 4: Compute Error
> Error=y^−y

5. Step 5: Update Weights
Use gradient descent rule.

6. Step 6: Repeat
Continue for multiple epochs until convergence.

# Given Truth Table
| (in1) | (in2) | Output |
| ----- | ----- | ------ |
| 0     | 0     | 1      |
| 0     | 1     | 0      |
| 1     | 0     | 0      |
| 1     | 1     | 0      |
- This represents the NOR function.

1. (i) McCulloch–Pitts Neuron
- McCulloch–Pitts Model
The neuron output is:
```yml
y={ 1. ​if ∑wi​.xi​≥θ 
    0. otherwise​  } 
```
- Where:
    wi = weights
    θ = threshold
- Design for NOR Gate
- We want:
    Output = 1 only when both inputs are 0.
- Choose:
    w1​=−1,w2​=−1
- Threshold:
>   θ=−0.5

- Verification
- Case 1
    x1​=0, x2​=0
    - Net input:
    - (−1)(0)+(−1)(0)=0
    0≥−0.5
    - Output:
    - y=1
    Correct.
- Case 2
x1​=0, x2​=1
..

- Case 3
x1​=1, x2​=0
...

- Case 4
x1​=1, x2​=1
...

- Final MCP Solution
> w1=−1,w2=−1,θ=−0.5
	​
2. (ii) Perceptron Model
- Given:
    - Initial weights:
        w1=w2=1
    - Bias:
        b=1
    - Learning rate:
        α=0.1

- Perceptron Learning Rule
- Net input:
    > yin=b+w1x1+w2x2
- Activation:
```yml
y={ 1  ​yin​>0 
    0  yin​≤0​   }
```
- Weight update:
> wi(new)=wi(old)+α(t−y)xi
- t−y= actual - prediction value of w.

- Bias update:
> b(new)=b(old)+α(t−y)

- Initial Values
w1=1,w2=1,b=1

## Training
- Pattern 1
- Input:
(0,0),t=1
- Net input:
    yin=1
- Output:
    y=1
Correct.
No update.

- Pattern 2
Input:
(0,1),t=0
- Output:
    y=1
- Error:
    t−y=0−1=−1
- Update
    - w1
    w1=1+0.1(−1)(0)=1
    - w2
    w2=1+0.1(−1)(1)=0.9
    - Bias
    b=1+0.1(−1)=0.9

- Pattern 3
Input:
(1,0),t=0
...

- Pattern 4
Input:
(1,1),t=0
...
- Final Perceptron Parameters After One Epoch
w1=0.8,w2=0.8,b=0.7
	​
# Perceptron and Multilayer Perceptron (MLP)
1. Perceptron Model
- A Perceptron is the simplest type of artificial neural network used for binary classification problems.
- It was introduced by Frank Rosenblatt in 1958.
- Structure of Perceptron
    - A perceptron contains:
        - Input layer
        - Weights
        - Summation unit
        - Activation function
        - Output
- Working of Perceptron
- The perceptron computes a weighted sum of inputs:
> yin=b+(i=1->n)∑wi.xi
- Where:
    - xi = inputs
    - wi = weights
    - b = bias

- Activation Function
    - The perceptron uses a step activation function:
    ```yml
    y={ 1   ​yin​≥0
        0   yin​<0​  }
    ```
- Diagram of Perceptron
```yml
x1 ----\
x2 ----- > Summation + Activation → Output
x3 ----/
```
- Learning Rule
- Weights are updated using:
    > 𝑤i​(new)=wi​(old)+α(t−y)xi​
- Where:
    α = learning rate
    t = target output
    y = predicted output
- Example: AND Gate Using Perceptron
| (x_1) | (x_2) | Output |
| ----- | ----- | ------ |
| 0     | 0     | 0      |
| 0     | 1     | 0      |
| 1     | 0     | 0      |
| 1     | 1     | 1      |

- Advantages of Perceptron
    Simple and fast
    Easy implementation
    Works for linearly separable problems
- Limitations of Perceptron
    Cannot solve nonlinear problems
    Fails for XOR gate
    Uses hard threshold activation

2. 2. Multilayer Perceptron (MLP)
- A Multilayer Perceptron is an advanced neural network containing:
    - Input layer
    - One or more hidden layers
    - Output layer
- MLP overcomes the limitations of a single perceptron.
- Structure of MLP
> Input Layer → Hidden Layer(s) → Output Layer
- Each neuron is connected using weighted links.
- Working of MLP
1. Step 1: Forward Propagation
Inputs move through layers.
Each neuron computes:
> z=∑wi​xi​+b
- Activation functions like:
    Sigmoid
    ReLU
    Tanh
are applied.
- Sigmoid Activation
> σ(z)=1​/1+e^−z

2. Step 2: Compute Error
Difference between actual and predicted output.

3. Step 3: Backpropagation
Error is propagated backward to update weights.
Gradient descent is used to minimize loss.

- Example: XOR Gate Using MLP
XOR truth table:
| (x_1) | (x_2) | Output |
| ----- | ----- | ------ |
| 0     | 0     | 0      |
| 0     | 1     | 1      |
| 1     | 0     | 1      |
| 1     | 1     | 0      |
- A single perceptron cannot solve XOR because it is not linearly separable.
An MLP with hidden layers can solve it successfully.

- Advantages of MLP
    Solves nonlinear problems
    Learns complex patterns
    High prediction accuracy
    Widely used in deep learning

- Disadvantages of MLP
    Computationally expensive
    Requires large training data
    Training may take longer

- Applications of MLP
    Image recognition
    Speech recognition
    Medical diagnosis
    NLP
    Recommendation systems

| Feature      | Perceptron         | Multilayer Perceptron |
| ------------ | ------------------ | --------------------- |
| Layers       | Single layer       | Multiple layers       |
| Hidden Layer | No                 | Yes                   |
| Problem Type | Linear             | Linear + Nonlinear    |
| Activation   | Step function      | Sigmoid/ReLU/Tanh     |
| XOR Problem  | Cannot solve       | Can solve             |
| Learning     | Simple update rule | Backpropagation       |
