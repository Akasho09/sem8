# PAPER 7
[text](<../R papers/dental research journal.pdf>)

Received: 20‑May‑2023
Revised: 30‑Oct‑2023
Accepted: 04‑Nov‑2023
Published: 27-Nov-2023

## Deep learning for tooth identification and enumeration in panoramic radiographs

### ⭐ 1. Goal of the Study
- The main aim is:
- ✅ Automatically identify teeth
- ✅ Automatically number teeth
from panoramic dental X-rays using deep learning.
- Tooth numbering is important because it is the first step in dental diagnosis and treatment planning.

### ⭐ 2. Problem Addressed
- Manual tooth identification:
    - ❌ Time-consuming
    - ❌ Prone to human error
    - ❌ Difficult with many teeth in one image
- Challenges in AI:
- Up to 32 tooth classes in one image
- Presence of non-tooth structures like:
    - Sinuses
    - Vertebrae
    - Jaw bones
- The paper solves this using a two-step deep learning approach.

### ⭐ 5. Proposed Architecture (Most Important)

1. 🧠 Step 1: Quadrant Detection Model
- Divide panoramic image into four mouth quadrants:
    - Upper left
    - Upper right
    - Lower left
    - Lower right
- ✔ Model Used
    - Faster R-CNN
    - Backbone: ResNet-50
- ✔ Output
    - Bounding boxes around each quadrant.

### ✔ Three Quadrant Detection Approaches Tested:
- 1️⃣ 4-class method
- 2️⃣ 2-class method
- 3️⃣ 1-class method
👉 1-class and 2-class methods achieved best results.


### 🧠 Step 2: Tooth Enumeration Model
- ✔ Input
    - Each quadrant image from Step 1.
- ✔ Model Used
    - Two separate Faster R-CNN models:
    - Upper jaw model
    - Lower jaw model
- ✔ Output
    - Tooth bounding box
    - Tooth number label
    - Confidence score

### ⭐ 6. Special Processing Step
- Right quadrants are flipped before training
- Reason:
    - Reduce alignment differences
    - Improve consistency
    - After prediction → flipped back.


### ⭐ 9. Results
- 🔥 Quadrant Detection
    - AP50 = 100%
- 🔥 Tooth Enumeration
    - Upper quadrants AP ≈ 95.93%
    - Lower quadrants AP ≈ 95.05%

