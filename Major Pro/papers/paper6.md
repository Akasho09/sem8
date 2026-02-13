# PAPER 6
[text](<../R papers/automated permanent tooth deteection.pdf>)

- Vol. 137 No. 5 May 2024

## Automated permanent tooth detection and numbering on panoramic radiograph using a deep learning approach

###  🧠 Overall Approach
- The system uses Deep Learning object detection to:
- ✅ Detect each permanent tooth
- ✅ Assign correct tooth number
(From panoramic dental X-rays)

### 
2. 📌 Ground Truth Annotation
- Each tooth is manually labeled by experts.
    - ✔ Bounding box drawn around each tooth
    - ✔ 32 tooth classes used
    - ✔ Universal numbering system applied

3. 📌 Annotation Format
- Each annotation contains:
- Tooth class ID
- Center coordinates
- Bounding box width
- Bounding box height

### ⭐ 2️⃣ Model Architecture – YOLOv4
- YOLOv4 detects teeth using three major parts

1. 🧩 A. Backbone (Feature Extraction)
- Uses:
    - 👉 CSP-Darknet53 network
- Purpose:
    - Extracts tooth features
    - Learns tooth shapes and patterns

2. 🧩 B. Neck (Feature Fusion)
- Uses:
    - ✔ Spatial Pyramid Pooling (SPP)
    - ✔ Path Aggregation Network (PAN)
- Purpose:
    - Combines multi-scale features
    - Helps detect teeth of different sizes

3. 🧩 C. Head (Prediction Layer)
- Uses YOLO detection layer.
- Predicts:
    - Tooth location
    - Tooth class number
    - Bounding box coordinates


### ⭐ Final Results
- ✔ Accuracy → 88.5%
- ✔ Precision → 87.7%
- ✔ Recall → 100%
- ✔ F1 Score → 93.44%

### Workflow
```yml

Panoramic X-ray
      ↓
Bounding Box Annotation
      ↓
YOLOv4 Training
      ↓
Feature Extraction
      ↓
Tooth Detection + Numbering
      ↓
Evaluation using Confusion Matrix
```


