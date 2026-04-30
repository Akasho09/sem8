# 🔹 Word:
> computational
- 🔹 Apply **Porter Stemming** (intuitively):
computational → computation (remove -al)
computation → computate (rule-based transformation)
computate → comput (remove -ate)

- 🔹 Final Stem:
👉 comput

## Porter stemmimg algo :
- A consonant is a letter other than A E I O U and Y which isnt proceceed by consonant.
- EXMAPLE : 
SYZYGY ==> consonsnts are S Z and G .

- Words are represneted as :
> C (VC)^m V
- Measure (m)
- 👉 It counts vowel-consonant patterns in a word
- This helps decide whether to remove a suffix or not


## 

| Original Word | Stemmed Word |
| ------------- | ------------ |
| The           | the          |
| quick         | quick        |
| brown         | brown        |
| foxes         | **fox**      |
| jumped        | **jump**     |
| over          | over         |
| the           | the          |
| lazy          | **lazi**     |
| dog           | dog          |

- foxes → fox (plural removal)
- jumped → jump (past tense removed)
- lazy → lazi ❗ (Porter converts y → i)

