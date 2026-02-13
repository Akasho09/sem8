# PAPER 8
[text](<../R papers/dmfr.pdf>)

## Deep learning for automated detection and numbering of permanent teeth on panoramic images

### ⭐ 1. Goal of the Study
- The main objective is:
- ✅ Automatically detect teeth
- ✅ Automatically assign tooth numbers
from panoramic dental X-rays (OPG images).
- This helps automate dental charting, which is an essential step in diagnosis and treatment planning.

### ⭐ 2. Problem Addressed
- Manual tooth numbering has limitations:
    - ❌ Time-consuming
    - ❌ Subject to human error
    - ❌ Difficult due to:
        - Noise in X-rays
        - Overlapping teeth
        - Similar tooth structures
- The paper solves this using a three-step deep learning system.
    
### ⭐ 4. Proposed Architecture (Most Important)
- The system uses three CNN modules.

1. 🧠 Step 1: ROI Detection (Tooth Region Segmentation)
- ✔ Model Used
    - 👉 U-Net (Semantic segmentation CNN)
- ✔ Purpose
    - Detect tooth region inside panoramic image
    - Remove unnecessary background structures
- ✔ How It Works
    - Converts image → pixel classification → segmentation mask
    - Generates bounding box covering entire teeth region
- ✔ Performance
    - IoU ≈ 0.70
(Overlap between predicted tooth region and actual region)

2. 🧠 Step 2: Tooth Detection
- ✔ Model Used
- 👉 Faster R-CNN (Object detection network)

- ✔ How It Works
    - Uses Region Proposal Network (RPN)
    - Generates candidate tooth bounding boxes
    - Object detector confirms tooth presence
    - Final bounding box created around each tooth

3. ✔ Performance

Recall ≈ 0.99

Precision ≈ 0.99

3. 🧠 Step 3: Tooth Numbering / Classification
- ✔ Model Used
- 👉 VGG-16 CNN


### ✔ How It Works
- Cropped tooth images given to VGG-16
- Extracts features
- Softmax classifier assigns:
    - Tooth number
    - Probability score
- ✔ Performance
    - Recall ≈ 0.98
    - Precision ≈ 0.98
    - F1 Score ≈ 0.98


