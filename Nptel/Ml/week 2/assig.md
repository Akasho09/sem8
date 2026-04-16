## Ridge and Lasso Regression
-  are techniques used to prevent overfitting by adding a penalty to the model. This is called regularization.
- In normal linear regression:
    - Model may overfit (learn noise)
    - Coefficients can become very large
    - Sensitive to multicollinearity
> 👉 Ridge and Lasso fix this by penalizing large coefficients into cost function or error or SSE(sum of square error)

### 📌 1. Ridge Regression (L2 Regularization)
> Loss = ∑(y−y^​)^2 + λ∑wi^2​
- 🔍 Key idea:
    - Adds square of coefficients
    - Shrinks coefficients towards zero, but never exactly zero
- ✅ Properties:
    - Keeps all features
    - Good when all features are useful
    - Handles multicollinearity well


### 📌 2. Lasso Regression (L1 Regularization)
> Loss = ∑(y−y^​)2+λ∑∣wi​∣
- 🔍 Key idea:
    - Adds absolute value of coefficients
    - Can shrink some coefficients exactly to zero
- ✅ Properties:
    - Performs feature selection
    - Removes irrelevant features automatically
    - Produces sparse models

| Feature           | Ridge              | Lasso                  |
| ----------------- | ------------------ | ---------------------- |
| Penalty           | (w^2) (L2)         | |w| (L1)               |
| Coefficients      | Small, not zero    | Can become zero        |
| Feature Selection | ❌ No              | ✅ Yes                  |
| Best when         | Many small effects | Few important features |

