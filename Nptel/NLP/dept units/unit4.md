# 

## 🔷 1. Pointwise Mutual Information (PMI)
PMI measures how strongly two events (words) are associated compared to if they were independent.
> PMI(x,y)=log P(x,y) / P(x)P(y)
- 🧠 Intuition
If x and y occur together more than expected → PMI is positive
If independent → PMI = 0
If rarely together → PMI is negative

| PMI Value | Meaning                     |
| --------- | --------------------------- |
| > 0       | Strong association          |
| = 0       | Independent                 |
| < 0       | Weak / negative association |


## Skip-gram Model
- Given a center word, predict its context (neighboring) words.
- Skip-gram asks:
    “Given this word, what words appear around it?”

### ⚙️ How it Works
- Each word → vector (embedding)
- Model learns vectors such that:
👉 words appearing in similar contexts have similar embeddings

- 👉 Cost = O(V) (very slow for large vocabulary)

- 📌 Parameters:
- Two matrices:
    - Input embedding: V×d
    - Output embedding: V×d
> Total=2×V×d

## 🔷 2. Negative Sampling (Optimization Trick)
- 📌 Problem:
Softmax over large vocabulary is expensive
- Instead of updating all words in vocabulary, update:
    1 positive example
    k negative (random) examples

### 🧠 Intuition
- Train model like a binary classifier:
- “Is this context word correct for the center word?”

### 📖 Example
- Center word = “brown”
- Correct context = “fox”
- Now sample wrong (negative) words:
“table”, “car”, “music”
- Training becomes:
(brown, fox) → 1 (positive)
(brown, table) → 0 (negative)
(brown, car) → 0
(brown, music) → 0

### ⚡ Why it’s Efficient
- Instead of updating all V words
👉 update only k+1 words
👉 Complexity becomes O(k) (k ≈ 5–20)

| Feature        | Skip-gram             | Negative Sampling      |
| -------------- | --------------------- | ---------------------- |
| Type           | Model                 | Optimization technique |
| Goal           | Predict context words | Simplify training      |
| Complexity     | High (softmax over V) | Low (k samples only)   |
| Output         | Word embeddings       | Same embeddings        |
| Used Together? | ✅ Yes                 |                        |

## Cosine Similarity
> cos(θ)= A⋅B/ ∣∣A∣∣∣∣B∣∣ 
​
| Value | Meaning                       |
| ----- | ----------------------------- |
| 1     | Same direction (very similar) |
| 0     | Unrelated                     |
| -1    | Opposite                      |
