# Given Neural Network
- We have:
    Inputs: x1,x2
    Hidden neurons: b11,b12
    Output neuron: b21
- Activation function: Linear
- Loss function: Mean Squared Error (MSE)
- Need to calculate:
    ∂L/∂w for all weights
    ∂L/∂b for all biases

1. Step 1: Forward Propagation Equations
- Hidden Layer
- Neuron b11
    - z11​=w11^1.​x1​+w21^1.​x2​+b11​
    - Since activation is linear:
    a11=z11
- Neuron b12
    - z12=w121x1+w221x2+b12
    a12=z12
- Output Layer
    - z21=w11^2.a11+w21^2.a12+b21
- Output:
    y=z21
	
2. Step 2: Loss Function
- Using MSE:
> L=1/2(t−y)^2
- Where:
t = target output
y = predicted output

3. Step 3: Derivative of Loss wrt Output
- Using chain rule:
> ∂L/∂y=−(t−y)=(y−t)
- Define:
δ=(y−t)

4. Step 4: Gradients for Output Layer Weights
    1. Gradient wrt w11^2
    > ∂L/∂w11^2=∂L/∂y.∂y/∂w11^2
    - using chain rule
    - since
        y=w11^2.​a11​+w21^2.​a12​+b21​
    => ∂y/∂w11^2=a11
    - Thus:
    > ∂L/∂w11^2​=(y−t)a11
        
    2. Gradient wrt w21^2
    ...​
    ​
5. Step 5: Gradient wrt Output Bias
    ∂y/∂b21=1
    - Hence:
    > ∂L/∂b21=(y−t)

6. Step 6: Gradients for Hidden Layer Weights
    1. Gradient wrt w11^1
    - ​Using chain rule:
    > ∂L/∂w11^1=∂L/∂y.∂y/∂a11.∂a11/∂w11^1
    - Now:
    ∂y/∂a11=w11^2
    - and
    ∂a11/∂w11^1=x1
    => ∂L/∂w11^1=(y-t).w11^2.x1

    2. Gradient wrt w21^1
    ....

    3. Gradient wrt w12^1
    ...

    4. Gradient wrt w22^1
    ...

7. Step 7: Gradients for Hidden Biases
    1. Bias b11 
    ∂L/∂b11=(y−t)w11^2
        ​
    2. Bias b12
    ....

# same q
 ![alt text](<Screenshot 2026-05-07 at 11.46.53 PM.png>)
 ![alt text](<Screenshot 2026-05-07 at 11.46.59 PM.png>) 
 ![alt text](<Screenshot 2026-05-07 at 11.47.07 PM.png>) 
​![alt text](<Screenshot 2026-05-07 at 11.47.13 PM.png>)
	
# Q5 (b) Factors Affecting the Performance of an Artificial Neural Network (ANN)
- The performance of an Artificial Neural Network depends on several factors related to:
    Data
    Network architecture
    Training process
    Hyperparameters
- These factors determine:
    Accuracy
    Training speed
    Generalization capability
    Stability of the model
1. Quality and Quantity of Data
- ANN performance highly depends on the dataset used for training.
- Important Aspects
    Sufficient training samples
    Clean and noise-free data
    Balanced classes
    Correct labeling
- Effect
- Poor-quality data leads to:
    Overfitting
    Underfitting
    Low prediction accuracy

2. Feature Selection and Feature Engineering
- Relevant input features improve learning capability.
- Good Features
    Capture useful patterns
    Reduce redundancy
    Improve convergence
    Effect
- Irrelevant features increase:
Complexity
Training time
Error rate

3. Network Architecture
    Architecture includes:
    Number of hidden layers
    Number of neurons
    Connection structure
- Hidden Layers
    Too few → underfitting
    Too many → overfitting and high computation
- Number of Neurons
    Small number may miss patterns
    Large number may memorize noise

4. Activation Function
- Activation functions introduce nonlinearity.
- Common functions:
    Sigmoid
    Tanh
    ReLU
    Leaky ReLU
    Effect
- Wrong activation may cause:
    Vanishing gradients
    Slow learning
    Dead neurons
- Example:
ReLU(x)=max(0,x)

5. Learning Rate
Learning rate controls weight updates during training.
Weight update rule:
    w:=w−η
    ∂w
    ∂L
- Where:
- η = learning rate
- Effect
    Very high → unstable training
    Very low → slow convergence
- Optimal learning rate gives stable and fast learning.

6. Weight Initialization
Initial weights affect convergence behavior.
Poor Initialization
Causes vanishing/exploding gradients
Slows training
Good Initialization
Xavier Initialization
He Initialization
improve convergence.

7. Loss Function
Loss function measures prediction error.
Examples:
    Mean Squared Error (MSE)
    Cross Entropy Loss
- Wrong loss function may reduce learning effectiveness.

8. Optimization Algorithm
- Optimization algorithms update weights efficiently.
- Examples:
    Gradient Descent
    SGD
    Adam
    RMSProp
    Effect
- Better optimizers:
    Speed up convergence
    Improve stability

9. Overfitting and Underfitting
Overfitting
Model memorizes training data.
Underfitting
Model fails to learn patterns.
- Prevention Techniques
    Dropout
    Regularization
    Cross-validation
    Early stopping
10. Batch Size and Epochs
- Batch Size
Number of samples processed together.
- Small Batch
    Noisy updates
    Faster learning
- Large Batch
    Stable updates
    Higher memory use
- Epochs
Number of complete passes through training data.
Too many epochs may cause overfitting.

11. Regularization Techniques
Used to improve generalization.
- Examples:
L1 Regularization
L2 Regularization
- Dropout
Example:
L=L0+λ∑w2

12. Hardware and Computational Power
- Training deep neural networks requires:
    GPUs
    TPUs
    Large memory
- Better hardware improves:
    Speed
    Scalability

13. Data Normalization
Scaling input data improves convergence.
- Techniques:
    Normalization
    Standardization
- Benefits:
    Faster training
    Stable gradients

14. Training Time
Insufficient training causes poor learning.
Excessive training may lead to overfitting.

| Factor                | Effect on ANN               |
| --------------------- | --------------------------- |
| Data Quality          | Accuracy and generalization |
| Learning Rate         | Convergence speed           |
| Architecture          | Model capacity              |
| Activation Function   | Nonlinear learning          |
| Optimizer             | Training efficiency         |
| Regularization        | Overfitting control         |
| Batch Size            | Stability and memory        |
| Weight Initialization | Gradient flow               |

# Q5 (c) Short Notes
1. (a) Vanishing Gradient Problem
- The Vanishing Gradient Problem occurs when gradients become extremely small during backpropagation in deep neural networks.
- As gradients move backward through layers:
    Weight updates become tiny
    Early layers learn very slowly
- Causes
    Deep networks
    Sigmoid/Tanh activation functions
- Effects
    Slow training
    Poor accuracy
    Failure to learn long-term dependencies
- Solutions
    ReLU activation
    Batch normalization
    Residual networks (ResNet)
    Proper initialization

2. (b) Convolutional Layer
- A Convolutional Layer is the core layer of a Convolutional Neural Network (CNN).
- It extracts important features from input images using filters (kernels).
- Convolution Operation
    - A filter slides over the image and computes feature maps.
- Formula:
- Feature Map=Input∗Kernel
- Functions
    Edge detection
    Pattern extraction
    Texture recognition
- Advantages
    Parameter sharing
    Reduced computation
    Spatial feature learning
- Applications
    Image recognition
    Face detection
    Medical imaging

3. (c) Max Pooling in CNN
Max Pooling is a downsampling technique used in CNNs.
It reduces spatial dimensions by selecting the maximum value from a region.
- Example
For a 2×2 region:
[
1 2
5 3
]
- Max pooling output:
5
- Advantages
    Reduces computation
    Controls overfitting
    Preserves important features
- Applications
    CNN architectures
    Image classification

4. (d) ReLU and Leaky ReLU Activation Function
- ReLU (Rectified Linear Unit)
- Formula:
    ReLU(x)=max(0,x)
- Advantages
    - Fast computation
    - Reduces vanishing gradient problem
- Limitation
    Can suffer from:
    Dying ReLU problem
where neurons stop learning for negative inputs.
- Leaky ReLU
    Leaky ReLU allows a small gradient for negative values.
- Formula:
    - LeakyReLU(x)=max(0.01x,x)
- Advantages
    - Prevents dead neurons
    - Better gradient flow

| Feature             | ReLU                  | Leaky ReLU  |
| ------------------- | --------------------- | ----------- |
| Negative Inputs     | 0                     | Small slope |
| Dead Neuron Problem | Possible              | Reduced     |
| Gradient Flow       | Limited for negatives | Better      |

5. (b) Early Stopping
- Early stopping is a regularization technique used to prevent overfitting.
- Training stops when validation error begins increasing.
- Working
    Monitor validation loss
    Stop training if performance degrades
- Advantages
    Reduces overfitting
    Saves computation time
    Improves generalization
- Applications
    Deep learning
    CNNs
    RNNs

6. (c) Dropout Layer
Dropout randomly deactivates neurons during training.
- Example:
    Dropout rate = 0.5
    Half of neurons are temporarily ignored
- Purpose
    Prevent overfitting
    Reduce neuron dependency
- Advantages
    Better generalization
    Reduces co-adaptation
- Applications
    Deep neural networks
    CNNs

7. (d) Activation Functions Used in Deep Learning
Activation functions introduce nonlinearity into neural networks.
Common Activation Functions
1. Sigmoid
> σ(x)=1/1+e^−x
- Range:
- 0 to 1
- Used in binary classification.

2. Tanh
- Range:
−1 to 1
- Zero-centered activation.

3. ReLU
ReLU(x)=max(0,x)
Most popular in deep learning.

4. Leaky ReLU
LeakyReLU(x)=max(0.01x,x)
Avoids dead neuron problem.

5. Softmax
Used for multiclass classification.
> P(y=i)=​e^zi/​​∑j.​e^zj
	​
