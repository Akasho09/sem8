# What is the effect of learning rate parameter on cost function and weights? 
- The learning rate (α) controls how big a step Gradient Descent takes while updating weights. Its effect is very important on both the cost function and the weights.
> θ=θ−α∇J(θ)

1. 🔹 Effect on Cost Function
    - ✅ Small Learning Rate (α ↓)
    Cost decreases slowly
    Takes many iterations to converge
    Stable and smooth convergence
    - 👉 Safe but very slow

- ⚠️ Large Learning Rate (α ↑)
    - Cost may:
    Decrease very fast (if chosen well)
    Overshoot minimum → oscillations
    Even diverge (increase instead of decrease)
    - 👉 Risky but fast

2. 🔹 Effect on Weights (Parameters)
- Small α:
Weights update very slightly
Gradual learning
May get stuck in local minima (slow escape)

- Large α:
Weights change drastically
May jump over optimal values
Can become unstable (values keep fluctuating)

| Learning Rate | Effect on Cost Function | Effect on Weights    |
| ------------- | ----------------------- | -------------------- |
| Too Small     | Slow decrease           | Tiny updates         |
| Optimal       | Fast convergence        | Stable updates       |
| Too Large     | Oscillation/divergence  | Large unstable jumps |


# 📊 Confusion Matrix Terms

| Term                | Formula                | Meaning          |
| ------------------- | ---------------------- | ---------------- |
| TP (True Positive)  | Predicted 1 & Actual 1 | Correct positive |
| TN (True Negative)  | Predicted 0 & Actual 0 | Correct negative |
| FP (False Positive) | Predicted 1 & Actual 0 | Wrong positive   |
| FN (False Negative) | Predicted 0 & Actual 1 | Missed positive  |


# 📈 Evaluation Metrics Formula Table

| Metric                        | Formula                                                     | Key Idea                                    |
| ----------------------------- | ----------------------------------------------------------- | ------------------------------------------- |
| **Accuracy**                  | (\frac{TP + TN}{TP + TN + FP + FN})                         | Overall correctness                         |
| **Precision**                 | (\frac{TP}{TP + FP})                                        | How many predicted positives are correct    |
| **Recall (Sensitivity)**      | (\frac{TP}{TP + FN})                                        | How many actual positives are caught        |
| **Specificity**               | (\frac{TN}{TN + FP})                                        | How many negatives are correctly identified |
| **F1 Score**                  | (\frac{2 \cdot Precision \cdot Recall}{Precision + Recall}) | Balance of precision & recall               |
| **Error Rate**                | (\frac{FP + FN}{Total})                                     | Total mistakes                              |
| **False Positive Rate (FPR)** | (\frac{FP}{FP + TN})                                        | Type I error                                |
| **False Negative Rate (FNR)** | (\frac{FN}{FN + TP})                                        | Type II error                               |

## 🔥 Which metric is NOT good here?
- 👉 Accuracy is NOT a good evaluation metric
- Why?
This is a real-world problem (water shortage) → missing a shortage (FN) is serious.
Accuracy treats all errors equally.
It may give high value even if important cases are misclassified.

- 👉 Example here:
- FN = 5 (schools wrongly predicted as no shortage ❗)
- This is critical but accuracy still looks high (90%)
- ✅ Better Metrics:
Recall → ensures we catch most shortage cases
> F1 Score → balances precision & recall

## 