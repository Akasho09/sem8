## PAPER 5
[text](<../R papers/Assessment_of_the_Impact_of_Missing_Teeth_on_Deep_Learning-Based_Tooth_Numbering_Method_From_Panoramic_X-Rays.pdf>)

- Received 19 February 2025, 
- accepted 12 March 2025, date of 
- publication 17 March 2025, date of current version 26 March 2025.

### Assessment of the Impact of Missing Teeth on Deep Learning-Based Tooth Numbering Method From Panoramic X-Rays

- The paper studies how AI performs tooth numbering on panoramic X-rays, especially when missing teeth are present.

- According to the pipeline diagram on page 4, the system works in three major stages:
1. ⭐ 1️⃣ Model Training
- 📌 Dataset Used
- Two datasets:
- ✔ Training Dataset
    - Tufts Dental Database (TDD)
    - 885 panoramic X-rays
2. ✔ Testing Dataset
    - Osaka University Dental Dataset (OUD)
    - 307 panoramic X-rays

- 📌 Tooth Labels
- Teeth are numbered using the FDI numbering system
- Each tooth gets:
    - Bounding box
    - Tooth number label

### 📌 Data Balancing
- Images are grouped into 8 tooth-count categories based on number of teeth present.
- 👉 Helps model learn from:
    - Full dentition images
    - Missing tooth cases

### ⭐ 2️⃣ Tooth Detection Phase
- The paper tests three object detection models:
    - ✔ YOLOv8
    - ✔ YOLOv11
    - ✔ RT-DETR

### 🧩 How Detection Works
1. Step 1: Input Panoramic X-ray
- Image is given to trained model.

2. Step 2: Bounding Box Prediction
- Model detects each tooth by:
    - Locating tooth region
    - Drawing bounding box
    - Assigning tooth number label
    - Giving confidence score

3. Step 3: Multiple Predictions Problem
- Sometimes:
    - 👉 Model creates multiple boxes for one tooth
    - 👉 Causes wrong numbering

### ⭐ 3️⃣ Detection Result Filtering
- To solve overlapping predictions:
    - ✔ Overlapping boxes are compared
    - ✔ Box with highest confidence score is selected
    - ✔ Remaining boxes are removed
- This ensures:
    - One tooth → One label
    - Improved numbering accuracy


### ⭐ Key Results
- ✔ More Teeth → Better Accuracy
    - Numbering accuracy improves as tooth count increases.

- ✔ Low Tooth Count → Poor Performance
    - Accuracy dropped to ~49% in lowest tooth group.

- ✔ Natural Teeth Perform Best
    - Teeth not near missing areas showed highest accuracy.

- ✔ Implants Cause Errors
    - Implants differ in shape from natural teeth.

### 🎯 Final Pipeline Summary
```yml
Panoramic X-ray
       ↓
Deep Learning Detection Model
(YOLO / RT-DETR)
       ↓
Bounding Box + Tooth Number
       ↓
Overlapping Box Filtering
       ↓
Final Tooth Numbering Output
```

### 🔥 Most Important Exam / Viva Points
👉 Uses object detection models
👉 Detects teeth using bounding boxes
👉 Uses FDI numbering system
👉 Missing teeth reduce AI accuracy
👉 Overlapping box filtering improves results


