# 
1. ✅ Vocabulary (V)
- Words:
> {i, want, to, eat, Chinese, food, lunch, spend}
- 👉 V=8


2. 🔹 (a) Calculate P(to∣want) and P(to∣i want)
- From table:
C(want, to)=608
C(want)=927
- P(to∣want)= 608+1​  /  927+8 ​≈0.651

3. 
P(I want to eat Chinese food)
- Using bigram model:
> P=P(i)⋅P(want∣i)⋅P(to∣want)⋅P(eat∣to)⋅P(Chinese∣eat)⋅P(food∣Chinese)

P≈2541828​×935609​×2425687​×75417​×16683​ === 👉 ≈ 0.00067 (very small, expected)

4. P(I want to eat English food)
- 👉 Problem:
“English” is NOT in vocabulary
> P(English∣eat)= 1 / 754

P=P(i)⋅P(want∣i)⋅P(to∣want)⋅P(eat∣to)⋅P(English∣eat)⋅P(food∣English)	​

- But:
> P(food∣English)= 1/V = 1/8	​

- P≈2541828​×935609​×2425687​×7541​×81​ <<< P(I want to eat Chinese food)


# “The quick brown fox jumps over the lazy dog.
The lazy dog sleeps all day.
The quick brown fox never jumps over the sleeping cat.”


1. 🔹 (ii) Probability of Sentence
“The quick brown fox jumps over the sleeping cat”
> P=P(The)⋅P(quick∣The)⋅P(brown∣The,quick)⋅P(fox∣quick,brown)
⋅P(jumps∣brown,fox)⋅P(over∣fox,jumps)⋅P(the∣jumps,over)
⋅P(sleeping∣over,the)⋅P(cat∣the,sleeping)
> P=2/3​×1/3​=1/33​≈0.333

3. (iii) Perplexity
- Using:
> PP=P^-1/N
- Where:
P= 1/3
N=9 words
- PP≈1.13



# 

1. 🔹 (a) Morphology
- Morphology is the study of the structure of words and how they are formed using morphemes (smallest meaningful units).
- Examples:
---
unhappiness → un + happy + ness
cats → cat + s
redo → re + do
---
👉 Shows how words are built and modified.

2. 🔹 (b) Orthography
- Orthography is the study of the correct spelling and writing system of a language.
- Examples:
Correct: receive ✅ vs Wrong: recieve ❌
The quick brown fox jumps over the lazy dog (correct sentence)
Capitalization: india ❌ → India ✅
- 👉 Focuses on spelling rules and writing conventions.

3. 🔹 (c) Phonology
- Phonology is the study of sounds in a language and how they are organized and used.
- Examples:
cat /kæt/ vs bat /bæt/ (change in sound changes meaning)
Silent letters: knife → /naɪf/
Stress patterns: record (noun) vs record (verb)
- 👉 Deals with pronunciation and sound patterns.

| Topic       | Focus              | Example            |
| ----------- | ------------------ | ------------------ |
| Morphology  | Word formation     | un + happy + ness  |
| Orthography | Spelling & writing | receive vs recieve |
| Phonology   | Sounds             | cat vs bat         |

# 
1. Delete t and add c.
i n e c n t i o n
e x e c u t i o n

2. substitute rest 3 

==> 8 answer.

