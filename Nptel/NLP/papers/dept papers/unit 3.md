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
EXAMPLES:
- Bat → animal 🦇 / cricket bat 🏏
- Train (vehicle)
    The train arrived on time.
- Train (to teach/prepare)
    She trains athletes daily.

5. 🔹 (v) Is “train” polysemous?
- Polysemous describes words or signs that have multiple, related meanings.
- Related Meanings: Unlike homonymy (unrelated meanings), polysemous words share a conceptual or historical link.
- EXAMPLE : Head → head of a person, head of a department, head of a table.

👉 Answer: YES
- Reason:
“Train” has multiple meanings (vehicle, teaching, sequence)
These meanings are related conceptually (movement/process/sequence)

| Feature          | Polysemy              | Homonymy                      |
| ---------------- | --------------------- | ----------------------------- |
| Meaning relation | Related               | Unrelated                     |
| Origin           | Same origin           | Different origins             |
| Example          | *Head*                | *Bat*                         |
| Memory trick     | “One idea, many uses” | “Same word, different worlds” |


##
- window size = 2 (around)

1. 👉 The cat sat on the mat 
> Feature vector = {The, cat, on, the}
- 👉 Often written as:
w−2=The
w−1=cat
w+1​=on
w+2	​=the

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

# 

1. 🔹 Step 1: Homonymy vs Polysemy
- 🔸 Homonymy
👉 Between:
- line² (physical)vs line³ (textual)
- Reason:
Physical object vs abstract linguistic unit
No direct semantic relation
> ✔ Hence → Homonyms

2. Polysemy
- ✅ Polysemy in line² (Physical meanings)
- All related by idea of:
👉 “extended connection/path”

| Meaning        | Relation           |
| -------------- | ------------------ |
| rope           | physical line      |
| telephone line | communication path |
| railway track  | transport path     |
| route          | directional path   |
- ✔ Same underlying concept → connection/extension

- ✅ Polysemy in line³ (Text meanings)
- All related by:
👉 “sequence/arrangement of words”
| Meaning        | Relation              |
| -------------- | --------------------- |
| row of words   | base meaning          |
| poem line      | structured row        |
| actor dialogue | spoken line           |
| sentence       | meaningful expression |
- ✔ Same concept → ordered linguistic sequence


# collocation + n-gram features
1. 🔹 Step 2: Collocation Features (Position-based)
- [w−3​,w−2​,w−1​,w+1​,w+2​,w+3​]
=[in,a,long,at,the,checkout]

2. 🔹 Step 3: Include N-gram Features
- 🔸 Bigrams (around "line")
(a, long)
(long, line)
(line, at)
(at, the)
(the, checkout)

- 🔸 Trigrams
(in, a, long)
(a, long, line)
(long, line, at)
(line, at, the)
(at, the, checkout)

3. 🔹 Step 4: Final Feature Vector
- ✅ Collocation (word-level)
[in,a,long,at,the,checkout]

- ✅ Bigrams
[(a,long),(long,line),(line,at),(at,the),(the,checkout)]

- ✅ Trigrams
[(in,a,long),(a,long,line),(long,line,at),(line,at,the),(at,the,checkout)]

- ✔ Collocation → nearby +-3 words
- ✔ N-grams → start from -3 and make bi and trigrams include word itself.


