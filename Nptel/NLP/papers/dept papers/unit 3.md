# 
1. 🔹 (i) Hypernym
Hypernym = a general category for given words
- 👉 For car, bus, train, bicycle
Answer: Vehicle / Transport

2. 🔹 (ii) Meronym of “bus”
Meronymy = parts of something
- 👉 Parts of a bus:
engine
wheel
seat
door
- Answer: e.g., wheel

3. 🔹 (iii) Synonym of “car”
- 👉 Words with similar meaning
- Answer:
automobile
vehicle

4. 🔹 (iv) Homonyms of “train”
- 👉 Same word, different meanings:
Train (vehicle)
The train arrived on time.
Train (to teach/prepare)
She trains athletes daily.

5. 🔹 (v) Is “train” polysemous?
👉 Answer: YES
- Reason:
“Train” has multiple meanings (vehicle, teaching, sequence)
These meanings are related conceptually (movement/process/sequence)

##
- window size = 2 (around)

1. 👉 The cat sat on the mat 
> Feature vector = {The, cat, on, the}

2. “The students sat quietly in the classroom during the exam” 
> (ii) Feature vector = {The, students, quietly, in}

## Sentence:
“…towels and clothes hang from a line overhead.”

1. ✅ Context words:
👉 {from, a, overhead}

2. 🔹 Step 3: Vocabulary (IMPORTANT)
👉 “Assume C as whole corpus”
- So vocabulary = all unique words in passage
- Example vocabulary (important ones):
{about, three, years, ago, he, nearly, gave, up, because, nothing, sell, now, shelves, full, towels, clothes, hang, from, a, line, overhead}

3. 🔹 Step 4: Bag-of-Words Vector
- Now create vector:
1 if word appears in window
0 otherwise

4. 
| Word     | Value |
| -------- | ----- |
| from     | 1     |
| a        | 1     |
| overhead | 1     |
| others   | 0     |

- 🎯 Final Answer (Exam Style)
1. 👉 Context window words:
{from, a, overhead}

2. 👉 Bag-of-words vector:
from = 1
a = 1
overhead = 1
all other words = 0

