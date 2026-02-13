# PAPER 4

## Angle Quest: Deep Learning Approach for Tooth Segmentation and Axial Inclination Measurement in Orthopantomogram Radiographs
The proposed system is an end-to-end deep learning + computer vision framework for:
- ✅ Tooth Segmentation
- ✅ Mesiodistal Axial Inclination Measurement

### 🧠 Overall System Architecture
- The framework consists of 5 major stages:
- 1️⃣ Data Acquisition
- 2️⃣ Preprocessing & Annotation
- 3️⃣ Instance Segmentation (Mask R-CNN)
- 4️⃣ Post-processing & Midpoint Detection
- 5️⃣ Axial Inclination Angle Calculation
- 6️⃣ Statistical Validation



### 🔥 Final Architecture Summary (Exam Ready)
👉 Mask R-CNN for instance tooth segmentation
👉 Morphological processing + CCA for midpoint extraction
👉 Vector-based geometric computation
👉 Dentist-defined reference plane
👉 Automated mesiodistal axial inclination measurement
👉 Statistical validation against manual method