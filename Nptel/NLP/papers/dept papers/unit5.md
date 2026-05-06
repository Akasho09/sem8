# 

## 🔹 Information Extraction (IE)
- Information Extraction is the process of automatically extracting structured information (like entities, relationships, events) from unstructured text.
- Example:
“Elon Musk founded SpaceX in 2002.”
- 
→ Person: Elon Musk
→ Organization: SpaceX
→ Relation: founded
→ Date: 2002

## 🔹 Named Entity Recognition (NER)
- NER is the task of identifying and classifying named entities in text into predefined categories such as:
    Person
    Organization
    Location
    Date
- Example:
“Barack Obama was born in Hawaii.”
👉 Person: Barack Obama
👉 Location: Hawaii

## 🔹 Relation Extraction (RE)
- Relation Extraction identifies relationships between entities in text.
- Example:
“Steve Jobs founded Apple.”
👉 (Steve Jobs — founded — Apple)

## ❓ Why Information Retrieval (IR) is NOT sufficient for IE?

| Feature       | Information Retrieval (IR)              | Information Extraction (IE)             |
| ------------- | --------------------------------------- | --------------------------------------- |
| Goal          | Retrieve relevant documents             | Extract structured facts                |
| Output        | Documents / text                        | Structured data (tables, triples)       |
| Understanding | Keyword-based                           | Semantic understanding                  |
| Example       | Search: “Apple founder” → returns pages | Extract: (Steve Jobs — founded — Apple) |

### 🔥 Explanation
1. IR only finds documents
    It tells where information might be
    It does NOT extract exact facts

2. No structured output
    IR returns full text, not usable structured data

3. Lacks deep understanding
Cannot identify entities or relationships

4. IE goes beyond IR
IE processes retrieved text and extracts meaning

# 🔹 What are Encoding Schemes in NER?
- Encoding schemes (or tagging schemes) define how labels are assigned to each token in a sentence to mark entity boundaries and types.
- 👉 They tell us:
Where an entity starts
Where it ends
What type it is (PER, ORG, LOC, etc.)

1. 🔹 1. IO Scheme (Inside–Outside)
- 📌 Tags:
    I-XXX → Inside an entity
    O → Outside any entity
- 📌 Example:
Sentence:
👉 “Barack Obama visited India”
| Word    | Tag   |
| ------- | ----- |
| Barack  | I-PER |
| Obama   | I-PER |
| visited | O     |
| India   | I-LOC |

- ⚠️ Limitation:
❌ Cannot distinguish start of entity
❌ Ambiguous for consecutive entities

2. BIO Scheme (Begin–Inside–Outside)
- 📌 Tags:
    B-XXX → Beginning of entity
    I-XXX → Inside entity
    O → Outside
- 
👉 “Barack Obama visited India”
| Word    | Tag   |
| ------- | ----- |
| Barack  | B-PER |
| Obama   | I-PER |
| visited | O     |
| India   | B-LOC |

- ✔ Advantages:
Clearly marks entity boundaries
Widely used

3. 🔹 3. BIOES Scheme (Begin–Inside–Outside–End–Single)
- 📌 Tags:
B-XXX → Beginning
I-XXX → Inside
O → Outside
E-XXX → End
S-XXX → Single-word entity
- 
| Word    | Tag   |
| ------- | ----- |
| Barack  | B-PER |
| Obama   | E-PER |
| visited | O     |
| India   | S-LOC |

- ✔ Advantages:
More precise boundaries
Helps models learn better

4. 🔹 4. BILOU Scheme (Begin–Inside–Last–Outside–Unit)
- 📌 Tags:
B → Begin
I → Inside
L → Last
O → Outside
U → Unit (single word entity)

- 📌 Example:
| Word    | Tag   |
| ------- | ----- |
| Barack  | B-PER |
| Obama   | L-PER |
| visited | O     |
| India   | U-LOC |

- 🔥 Comparison Table (Important)
| Scheme | Tags          | Precision | Use                 |
| ------ | ------------- | --------- | ------------------- |
| IO     | I, O          | Low       | Simple tasks        |
| BIO    | B, I, O       | Medium    | Most common         |
| BIOES  | B, I, O, E, S | High      | Advanced models     |
| BILOU  | B, I, L, O, U | High      | Equivalent to BIOES |

# Propose a supervised machine learning method to construct a Named Entity Recognizer for identification of Person names, Organization names and Location Names in a given corpus.
- 🔹 Goal
- Build a Named Entity Recognizer (NER) to identify:
    Person (PER)
    Organization (ORG)
    Location (LOC)
using a supervised machine learning method

1. Overall Approach
👉 Treat NER as a sequence labeling problem
👉 Use a supervised model like:
- Conditional Random Fields (CRF) ⭐ (most common in exams)
or BiLSTM-CRF (modern approach)

2. Data Preparation
- 📌 Step:
Collect a labeled corpus
- 📌 Example (BIO format):

| Word   | Tag   |
| ------ | ----- |
| Barack | B-PER |
| Obama  | I-PER |
| works  | O     |
| at     | O     |
| Google | B-ORG |
| in     | O     |
| USA    | B-LOC |

3. Feature Extraction
- For each word, extract features:
- 🔸 Word Features
    Current word
    Lowercase form
    Prefix / suffix
    Word shape (Xxxx, ALLCAPS)
- 🔸 Context Features
    Previous word
    Next word
    Previous tags (for CRF)
- 🔸 Orthographic Features
    Capitalization
    Digits
    Special characters
- 🔸 Linguistic Features
    Part-of-Speech (POS)
    Chunk tags

4. 🔹 4. Model Selection
    1. Option 1: Conditional Random Fields (CRF)
    Models sequence dependencies
    Avoids label inconsistency
    - Idea:
    > P(Y∣X)=1 / Z(X)  ​exp(∑λi​fi​(X,Y))

    2. Option 2: BiLSTM + CRF (Advanced)
    BiLSTM captures context
    CRF ensures valid label sequence

5. Training Phase
- Input: labeled sentences
Extract features
- Train model to learn:
Word → tag mapping
Tag transitions

6. Prediction Phase
- For new sentence:
Extract features
Apply trained model
Output entity tags

- Example:
- Input:
👉 “Microsoft hired John in London”
- Output:
Microsoft → ORG
John → PER
London → LOC

7. Evaluation
- Use:
Precision
Recall
F1-score

8. Advantages of Supervised Approach
✔ High accuracy
✔ Learns complex patterns
✔ Handles context

9. Limitations
❌ Requires labeled data
❌ Domain-dependent


# Construct a rule based e-mail extractor which can distinguish between sender and receiver e-mail addresses.
- A rule-based email extractor can be built using:
1. Regex to extract email patterns
> [A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}

2. Context-based rules using keywords like:
- Scan context window (±3 words)
```yml
if "from" near email → Sender
elif "to", "cc", "bcc" near email → Receiver
else → Unknown
```

### Example
- Input:
```yml
From: john@gmail.com  
To: alice@yahoo.com  
Cc: bob@gmail.com
```
Output:
```yml
Sender → john@gmail.com
Receivers → alice@yahoo.com
, bob@gmail.com
```

- Algorithm:
    Extract emails
    Check surrounding words
    Assign role based on rules

