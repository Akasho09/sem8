## PAPER 3
 
### TeethDE-GCNet: accurate tooth numbering in dental panoramic radiographs via detail-enhanced and context-aware detection

- 🦷 Automatic tooth detection and tooth numbering in panoramic dental X-ray images

### 🎯 Specifically, It Predicts:
1. 1️⃣ Tooth Location (Detection)
- Detects each tooth in the panoramic radiograph
- Draws bounding boxes around every tooth

2. 2️⃣ Tooth Number (Enumeration)
- Assigns the correct FDI tooth number to each detected tooth
- Works for:
    - Permanent teeth
    - Mixed dentition cases

3. 3️⃣ Handles Special Cases
- It can detect:
    - Missing teeth
    - Impacted wisdom teeth
    - Subtle residual roots
    - Small dental structures
    (Shown in visualization results on page 6)

### 📊 Performance
- The model achieves very high accuracy:
    - mAP50 ≈ 98.91%
    - Recall ≈ 98.07%
    - Precision ≈ 97.61%
(From Table 3 on page 6)

### Arch :
```yml
Input Panoramic X-ray Image
        ↓
Backbone
(DEConv + Feature Extraction)
        ↓
Neck
(C2f_CMU Context Fusion)
        ↓
Detection Head
(Multi-Scale Detection + Small Object Layer)
        ↓
Focaler-IoU Loss Optimization
        ↓
Non-Maximum Suppression
        ↓
Output:
Tooth Detection + Tooth Numbering
```


### 🔥 Difference from Previous Paper
| Previous Paper                      | This Paper                     |
| ----------------------------------- | ------------------------------ |
| Predicts dental diseases            | Predicts tooth numbers         |
| Classifies cavities, implants, etc. | Detects and numbers teeth      |
| Uses hybrid DL + LSTM               | Uses improved YOLOv8 detection |
