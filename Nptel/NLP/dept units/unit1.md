# 📘 Unit 1: Text Processing Tasks & Probabilistic Language Models

## 🔹 1. Introduction to Text, Speech & Language Technologies
- Text Processing: Handling written language (e.g., search engines, chatbots).
- Speech Processing: Deals with spoken language (e.g., voice assistants like Alexa).
- Language Technologies (NLP): Combines linguistics + AI to process human language.
- Applications:
    Machine Translation (Google Translate)
    Chatbots
    Sentiment Analysis
    Speech Recognition

## 🔹 2. Basic Text Processing Tasks
1. Tokenization
- Splitting text into words/sentences
Example:
"I love NLP" → [I, love, NLP]

2. Stop Word Removal
- Removing common words like is, the, and

3. Stemming
- Reduces word to root form
- Example:
    playing → play

4. Lemmatization
- Converts words into meaningful base form
- Example:
better → good

## 🔹 3. Normalization
- Standardizing text for processing
- Includes:
    Lowercasing
    Removing punctuation
    Expanding abbreviations
    "can't" → "cannot"

## 🔹 4. Max Match Algorithm (Word Segmentation)
- Used for languages without spaces (e.g., Chinese)
- Chooses longest matching word
Example:
Input: iloveindia
Output: i + love + india
- Steps:
    Start from beginning
    Match longest word in dictionary
    Repeat for remaining string

## 🔹 5. Porter Stemmer
- Popular stemming algorithm
- Removes suffixes based on rules
- Example:
    caresses → caress
    ponies → poni
    Key Idea:
- Applies multiple steps:
1. Step 1: Remove plural suffixes
2. Step 2: Remove -ed, -ing
3. Step 3: Reduce endings

## 🔹 6. Minimum Edit Distance (MED)
- Measures similarity between two strings
- Operations:
    Insert
    Delete
    Substitute
- Formula:
D(i,j)=min ⎧ D(i−1,j)+1 
           ⎨ D(i,j−1)+1
           ⎩ D(i−1,j−1)+cost
- Example:
- kitten → sitting → Distance = 3

## 🔹 7. Probabilistic Language Models
- Assign probability to a sentence
- Used in:
    Speech recognition
    Auto-complete

## 🔹 8. N-Gram Model
- Predicts word based on previous words
- Types:
Unigram → single word
Bigram → two words
Trigram → three words
- Formula:
P(w1,w2,...,wn)=∏i=1nP(wi∣wi−1,...,wi−(n−1))

## 🔹 9. Bigram Probabilities
- Uses 1 previous word
- Formula:
> P(wn​∣wn−1​)= Count(wn−1​,wn​)​ / Count(wn−1​) 
- Example:
I love NLP
→ P(love | I)

## 🔹 10. Perplexity
- Measures how good a language model is
- Lower = better
- Formula:
> PP(W)=​∏i->N (1/​P(wi​∣context)1​) ^1/N

## 🔹 11. Smoothing Techniques
- Used to handle zero probability problem
1. 🔸 1. Laplace (Add-One) Smoothing
> P=Count+1 / Total+V 
- Simple but not very accurate

2. Good-Turing Smoothing
Adjusts probabilities for unseen events
Uses frequency of frequencies

3. Kneser-Ney Smoothing (Important)
Most advanced smoothing
Considers context diversity

4. Interpolation
Combines multiple models
P=λ1.​Pbigram​+λ2.​Punigram​

## 🔹 Summary (Exam Quick Revision)
Text Processing → Tokenization, Stemming, Lemmatization
Normalization → Clean text
Max Match → Word segmentation
Porter Stemmer → Rule-based stemming
Edit Distance → String similarity
N-Gram → Predict next word
Bigram → Uses 1 previous word
Perplexity → Model quality
Smoothing → Fix zero probability
