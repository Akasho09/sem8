# PCA: Reduce 2D Space to 1D Space
| Feature | Example 1 | Example 2 |
| ------- | --------- | --------- |
| (X_1)   | 4         | 5         |
| (X_2)   | 6         | 9         |

1. Step 1: Form Data Matrix
X=[ 4 6
    ​5 9​]
- x1,x1 in col1 and x2,x2 in col2.

2. Step 2: Compute Mean of Each Feature
- Mean of X1: μ1​=4+5/2​=4.5
- Mean of X2: μ2​=6+9/2​=7.5
- Mean vector: μ=[4.5​  7.5​]

3. Step 3: Mean Center the Data
Subtract mean from each feature.
- Xcentered=
    [ 4−4.5  6−7.5
      5−4.5  9−7.5 ]

4. Step 4: Compute Covariance Matrix
> Cov(X)=1/n−1 X^T.X
- n=2.
Here:
- XT= [−0.5  ​0.5 
       −1.5  1.5 ​]
=> Cov=[ 0.5 1.5
         ​1.5 4.5​ ]
        
5. Step 5: Find Eigenvalues
> ∣C−λI∣=0
=> λ(λ−5)=0
- λ1​=5,λ2​=0
- Largest eigenvalue:
    > λ=5
	​
6. Step 6: Find Eigenvector for Largest Eigenvalue
> (C−5I)v=0
- v = [ x
        y ]
=> −4.5x+1.5y=0
=> Eigenvector:
v=[1
   3​]
- Normalize it:
- ∣∣v∣∣=1^2+3^2​=root(10)
​- Normalized principal component:
1/root(10) [1
            3]

- Final Principal Component (1D Direction)
PC1  =[ 0.316
        0.949 ]
	​
# Fisher Discriminant Ratio (FDR)
Fisher Discriminant Ratio is a measure used in Linear Discriminant Analysis (LDA) to evaluate how well two classes are separated.
- It tries to:
Maximize distance between class means
Minimize spread within each class
- Mathematically:
> J(w)= wT.SB.w/wT.SW.w 
- Where:
    - SB = Between-class scatter matrix
    - SW = Within-class scatter matrix
    - w = projection vector
- Given Data
    1. Class 1
        (2,1), (3,4)
    2. Class 2
        (6,5), (5,7)

1. Step 1: Compute Mean Vectors
- Mean of Class 1
- μ1​=[ 2+3/2   = [2.5 
       1+4/​2 ​​]    2.5​]
- Mean of Class 2
...

2. (i) Within-Class Scatter Matrix SW​
Formula:
> SW​=S1​+S2​
- For Class 1
    - Point (2,1)
    - `x−μ1`​=[ −0.5
               −1.5​]
    - Outer product:
            [ 0.25 0.75
            0.75 2.25 ]
    - Outer product is x.x^t or `(x−μ1)(x−μ1)^t`

    - Point (3,4)
    ...

- For Class 2
    - Point (6,5)
    ...
    - Point (5,7)
    ...

- Final Within-Class Scatter Matrix
> SW =.  [   0.5 1.5.     [ 0.5.  −1 ]
>           1.5 4.5 ]+.   −1.    2. ]
- S1 is same for both points in class1 and same in class2 , so pick 1.

3. (ii) Between-Class Scatter Matrix SB​
- Formula:
> SB=(μ1−μ2)(μ1−μ2)^T
- Difference:
μ1​−μ2​=[ −3
       −3.5​]
- SB =[ 9. 10.5
        10.5 12.25 ]

3. Projection Vector
- For LDA:
> w=Sw^−1(μ1−μ2)
- Inverse of SW:
SW^−1 = 1/6.25 [  6.5  −0.5
                  −0.5  1   ]
- Equivalent direction:
w=[ 2.56
    0.4  ]

- Final Answers
1. Sw
2. Sb
3. w

# (i) Methods for Feature Selection
- Feature selection is the process of selecting the most relevant features (variables) from a dataset to improve model performance and reduce complexity.
- Objectives of Feature Selection
    Reduce overfitting
    Improve model accuracy
    Reduce training time
    Remove irrelevant and redundant features
- Types of Feature Selection Methods
1. Filter Methods
- Features are selected based on statistical measures independent of machine learning algorithms.
- Techniques
    Correlation coefficient
    Chi-Square test
    Information Gain
    ANOVA
- Advantages
    Fast
    Computationally efficient
- Disadvantages
    Ignores interaction between features

2. Wrapper Methods
- Uses a machine learning model to evaluate feature subsets.
- Techniques
    Forward Selection
    Backward Elimination
    Recursive Feature Elimination (RFE)
- Advantages
    Better accuracy
- Disadvantages
    Computationally expensive

3. Embedded Methods
- Feature selection occurs during model training.
- Techniques
    Lasso Regression
    Decision Trees
    Random Forest Feature Importance
- Advantages
    Efficient and accurate
- Disadvantages
    Depends on chosen model
- Applications
    Text classification
    Image processing
    Medical diagnosis

# (ii) Crowding Problem in t-SNE(Stochastic Neighbor Embedding)
- The Crowding Problem is a limitation encountered in t-Distributed Stochastic Neighbor Embedding (t-SNE) during dimensionality reduction.
- It occurs when high-dimensional data points are mapped into a lower-dimensional space (usually 2D or 3D).
- Cause of Crowding Problem
- In high-dimensional space:
    Many points can remain far apart.
    But in low-dimensional space:
    There is insufficient space to preserve all pairwise distances.
- As a result:
    Distant points become crowded together.
    Global structure may be distorted.
- Effects
    Loss of global relationships
    Clusters may appear artificially close
    Difficult interpretation of distances between clusters
- How t-SNE Reduces Crowding
    - t-SNE uses a heavy-tailed Student’s t-distribution in low-dimensional space instead of Gaussian distribution.
- This allows:
    Better separation of distant points
    Improved visualization of clusters
- Applications of t-SNE
    Data visualization
    Image embeddings
    NLP embeddings
    Bioinformatics

# (iii) Significance of Covariance
- Covariance measures the relationship between two variables and indicates how they vary together.
- Covariance Formula
> Cov(X,Y)=∑(X−Xˉ)(Y−Yˉ)/n−1 
- Where:
    - Xˉ = mean of X
    - Yˉ= mean of Y
- Interpretation of Covariance

| Covariance Value | Meaning                              |
| ---------------- | ------------------------------------ |
| Positive         | Variables increase/decrease together |
| Negative         | One increases while other decreases  |
| Zero             | No linear relationship               |

- Significance of Covariance
1. Measures Relationship
Shows whether variables are positively or negatively related.

2. Basis for Correlation
Correlation is derived from covariance.

3. Important in PCA
PCA uses covariance matrix to identify directions of maximum variance.

4. Portfolio Analysis
In finance, covariance helps measure risk between assets.

5. Feature Dependency
Used in machine learning to identify dependent features.

- Advantages
    Helps understand data relationships
    Useful in dimensionality reduction

- Limitation
    Magnitude depends on variable scales, making interpretation difficult.

- Conclusion
    Feature selection improves efficiency and model accuracy.
    Crowding problem in t-SNE arises due to dimensionality reduction limitations.
    Covariance is an important statistical measure for analyzing relationships between variables.

# (i) Curse of Dimensionality
- The Curse of Dimensionality refers to problems that arise when the number of features (dimensions) in a dataset becomes very large.
- As dimensionality increases:
    Data becomes sparse.
    Distance measures become less meaningful.
    Machine learning algorithms become less efficient.
- The term was introduced by Richard Bellman.
- Effects of High Dimensionality
1. Sparse Data
Data points become widely scattered in high-dimensional space.

2. Increased Computational Cost
More dimensions require:
More memory
More processing time

3. Overfitting
Models may memorize noise instead of learning general patterns.

4. Distance Concentration
- Distances between points become very similar, reducing effectiveness of:
    KNN
    Clustering algorithms
- Example
    - In image processing:
        - Each pixel may act as a feature.
        - High-resolution images create thousands of dimensions.
- Solutions
    Feature Selection
    Dimensionality Reduction
    PCA
    t-SNE
    Regularization
- Applications
    Image recognition
    Text mining
    Bioinformatics

# (iii) Kullback–Leibler (KL) Divergence
- KL Divergence measures how one probability distribution differs from another probability distribution.
- It is widely used in:
    Machine Learning
    Information Theory
    Deep Learning
- Formula
Dkl(P∥Q)=∑P(x)logP(x)/Q(x)
- Where:
    P(x) = true probability distribution
    Q(x) = approximated distribution
- Interpretation
    Dkl=0: Distributions are identical.
    Larger value: Greater difference between distributions.
- Characteristics
    - Not symmetric:
    > Dkl​(P∣∣Q)=DKL​(Q∣∣P)
    - Always non-negative.
- Importance in Machine Learning
1. Used in t-SNE
Measures difference between high-dimensional and low-dimensional distributions.

2. Loss Function
Used in:
Variational Autoencoders (VAEs)
Probabilistic models
3. Distribution Comparison
Helps compare predicted and actual probability distributions.

- Applications
    NLP
    Deep Learning
    Recommendation Systems
    Statistical Modeling

- Conclusion
    Curse of dimensionality causes sparsity and computational challenges in high-dimensional data.
    t-SNE is a powerful visualization technique for reducing dimensions while preserving local structure.
    KL Divergence measures similarity between probability distributions and plays an important role in machine learning optimization.

