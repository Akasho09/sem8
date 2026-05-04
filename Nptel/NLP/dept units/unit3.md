# 📘 Unit 3: Lexical Semantics

## 🔹 1. Word Senses & Word Relations
- 📌 Word Sense
A word can have multiple meanings (polysemy)
- Example:
bank → river bank / financial bank
- 📌 Types of Word Relations
1. Synonymy (Same meaning)
big = large

2. Antonymy (Opposite)
hot ↔ cold

3. Hypernym (General term)
animal → dog

4. Hyponym (Specific term)
dog → animal

5. Meronymy (Part-of relation)
wheel → car

## 2. WordNet
- A lexical database grouping words into sets called synsets
- 📌 Features:
    Synsets (set of synonyms)
- Semantic relations:
Hypernym / Hyponym
Antonym
- Example:
Synset: {car, automobile}

## 🔹 3. Computing Word Similarity

### 🔸 3.1 Path-Based Similarity
- Based on distance in WordNet hierarchy
Idea:
👉 Shorter path → More similar

### 🔸 3.2 Information Content (IC)
Based on probability of concept
- Formula:
IC(c)=−logP(c)
- Insight:
Rare words → High IC → More informative

## 🔹 4. Word Sense Disambiguation (WSD)
- Selecting correct meaning of a word in context
- Example:
"He went to the bank"
River bank?
Financial bank?

## 🔹 5. Thesaurus-Based WSD (Using WordNet)
- Uses:
Synonyms
Related words
- Approach:
Compare context words with synsets
Choose most related sense

## 🔹 6. Lesk Algorithm (IMPORTANT)
- Choose sense with maximum overlap between:
    - Context words
    - Dictionary definition (gloss)
- Steps:
Get all meanings of word
Compare gloss with context
Select sense with highest overlap

## 🔹 7. Typical Features of WSD
Used in ML-based WSD:
    Surrounding words (context window)
    Part of Speech (POS)
    Collocations
    Syntactic patterns

## 🔹 8. Supervised WSD
- Train model using labeled data
- Steps:
    Input → word + context
    Train classifier
    Predict correct sense
- Pros:
✔ High accuracy
- Cons:
❌ Requires large labeled data

## 🔹 9. Semi-Supervised WSD
- Use:
Small labeled data
Large unlabeled data
- Methods:
Bootstrapping
Self-training

- 🔹 Quick Comparison Table

| Method          | Data Required | Accuracy |
| --------------- | ------------- | -------- |
| Lesk            | No training   | Medium   |
| Supervised      | Labeled data  | High     |
| Semi-supervised | Mixed data    | Good     |

## 🧠 Quick Revision (1-Min)
Word Sense → multiple meanings
WordNet → synsets + relations
Similarity → path + IC
WSD → choose correct meaning
Lesk → overlap-based
Supervised → labeled
Semi-supervised → mixed
