# 

## 🧠 What are Word Vectors?
- Word vectors (also called embeddings) are numerical representations of words in a vector (array) form so that machines can understand language.
- 👉 Each word is represented as a list of numbers:
"cat" → [0.2, -0.5, 0.8, ...]
"dog" → [0.25, -0.45, 0.75, ...]
- 👉 Words with similar meanings have similar vectors.

- Illustaration
![alt text](image-1.png)
- 👉 In this space:
cat and dog are close
king and queen are related
distance = similarity

### 🔹 Types of Word Vectors
1. Sparse Vectors
Mostly zeros
High dimensional (very large size)
- 👉 Example (Bag of Words):
Vocabulary = [cat, dog, apple, car]
"cat" → [1, 0, 0, 0]
"dog" → [0, 1, 0, 0]

2. Dense Vectors
Mostly non-zero values
Low dimensional (compact)
Learned using models like Word2Vec, GloVe
- 👉 Example:
"cat" → [0.21, -0.34, 0.78]
"dog" → [0.25, -0.30, 0.80]

| Feature    | Sparse Vector       | Dense Vector     |
| ---------- | ------------------- | ---------------- |
| Values     | Mostly 0s           | Mostly non-zero  |
| Size       | Very large          | Small            |
| Meaning    | No semantic meaning | Captures meaning |
| Example    | Bag of Words        | Word2Vec, GloVe  |
| Efficiency | Low                 | High             |

- 💡 Key Insight (Exam Line)
👉 Sparse vectors represent presence of words,
👉 Dense vectors represent meaning of words.

