# 📘 Unit 2: Text Classification & Sequence Modelling

## 1. Text Classification
- Assigning a category/label to a given text.
- Examples:
    Spam detection (Spam / Not Spam)
    Sentiment analysis (Positive / Negative)
    Topic classification (Sports / Politics)

### 🔸 1.1 Bag of Words (BoW)
- Represents text as a set of word frequencies
- Ignores grammar & word order
- Example:
    Text: "I love NLP and NLP loves me"
    Vocabulary → [I, love, NLP, and, loves, me]
    Vector → [1,1,2,1,1,1]
- Pros:
    ✔ Simple
    ✔ Works well for basic tasks
- Cons:
    ❌ Ignores context
    ❌ High dimensional

### 🔸 1.2 Conditional Independence Assumption
- Core idea of Naïve Bayes
- Assumes:
Words are independent given the class
- Mathematically:
> P(w1,w2,...,wn∣C)=i=1->n ∏ P(wi∣C)
- ⚠️ Not true in real language, but works surprisingly well

### 🔸 1.3 Multinomial Naïve Bayes Classifier
- Uses word frequencies for classification
- Formula:
> P(C∣d)= P(C)*∏i​P(wi​∣C)count(wi​)​ / P(d)
- Steps:
    Calculate prior P(C)P(C)P(C)
    Calculate likelihood P(w∣C)P(w|C)P(w∣C)
    Apply Bayes theorem
    Choose class with max probability

### 🔸 1.4 Maximum Likelihood Estimation (MLE)
- Estimates probabilities from data
- Formula:
> P(w∣C)=Count(w,C) / ∑w′Count(w′,C) 

### 🔸 1.5 Evaluation of Text Classification
Metrics:
- Accuracy = TP+TN / Total

- Precision

- Recall

- F1 Score

## 🔹 2. Sentiment Analysis

### 🔸 2.1 Types
1. Entity-Based
Sentiment about entity
Example:
"Amazon is great" → Positive

2. Aspect-Based
Sentiment about specific feature
Example:
"Camera is good but battery is bad"

### 🔸 2.2 Feature Extraction
Convert text → features
- Methods:
    - Bag of Words
    - TF-IDF
    - Word embeddings

### 🔸 2.3 Baseline Algorithm
- Count positive vs negative words

### 🔸 2.4 Sentiment Lexicons
- Dictionary of words with sentiment
- Example:
good → +1
bad → -1

### 🔸 2.5 Polarity Analysis
- Determines:
Positive
Negative
Neutral

### 🔸 2.6 Building Sentiment Lexicons
Methods:
Manual
Dictionary-based
Corpus-based

### 🔸 2.7 Semi-Supervised Algorithm
- Uses:
Small labeled data
Large unlabeled data

### 🔸 2.8 Turney Algorithm (Important)
- Uses:
PMI (Pointwise Mutual Information)
- Idea:
Compare association of words with:
"excellent"
"poor"

## 🔹 3. Sequence Modelling

### 🔸 3.1 Markov Models
Future depends only on present
- Formula:
P(Xn​∣X1​,...,Xn−1​)=P(Xn​∣Xn−1​)

### 🔸 3.2 Hidden Markov Model (HMM)
Components:
    States (hidden)
    Observations (visible)
    Transition probability
    Emission probability
    Applications:
    POS tagging
    Speech recognition

### 🔸 3.3 Inference in HMM
- 🔹 Greedy Search
Choose best at each step
❌ Not optimal

- 🔹 Beam Search
Keeps top k sequences
✔ Better than greedy

- 🔹 Viterbi Algorithm (IMPORTANT)
Finds most probable sequence
Formula:
> Vt​(j) = maxi​[Vt−1​(i)⋅aij​]⋅bj​(ot​)

### 🔸 3.4 Conditional Random Fields (CRF)
Improves HMM
Considers full sequence
- Advantage:
✔ No independence assumption
✔ Better accuracy

### 🔸 3.5 LSTM-based POS Tagging
Uses deep learning
Handles long dependencies
Why LSTM?
Remembers long context
Avoids vanishing gradient

# 🔹 Quick Revision Table   
| Topic       | Key Idea                 |
| ----------- | ------------------------ |
| BoW         | Word frequency           |
| Naive Bayes | Probabilistic classifier |
| MLE         | Estimate probability     |
| Sentiment   | Emotion detection        |
| Markov      | Depends on previous      |
| HMM         | Hidden states            |
| Viterbi     | Best sequence            |
| CRF         | Better sequence model    |
| LSTM        | Deep learning model      |
