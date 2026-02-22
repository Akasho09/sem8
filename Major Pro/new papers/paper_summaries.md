# Dental X-Ray Deep Learning Paper Summaries

---

## 1. Angle Quest: Deep Learning Approach for Tooth Segmentation and Axial Inclination Measurement in Orthopantomogram Radiographs

### Methodology

The paper proposes a fully automated deep learning + computer vision framework for:
1. Instance-level tooth segmentation
2. Automated mesiodistal axial inclination angle calculation

### Workflow

**1. Data Collection**
- 110 OPG radiographs
- Collected from A. B. Shetty Memorial Institute of Dental Sciences
- Age group: 18–30 years
- Ethical clearance obtained
- Sample size statistically validated

**2. Annotation Strategy**
- LabelMe-based polygon annotation
- Manual split-mask refinement (to separate overlapping roots of adjacent teeth)
- Converted into COCO format for Mask R-CNN training

**3. Data Augmentation**
- Horizontal flip, vertical flip, rotation (±15°), brightness/contrast adjustment, Gaussian blur
- 110 original + 220 augmented = **330 total images**

**4. Segmentation Model Selection**

*U-Net (Semantic Segmentation) — Rejected*
- Trained up to 130 epochs
- Failed on overlapping roots, low contrast regions, individual tooth separation

*Mask R-CNN (Instance Segmentation) — Final Model*
- Backbone: ResNet-50 + FPN
- Framework: Detectron2 (`mask_rcnn_R_50_FPN_3x`)
- Training: 1000 iterations, batch size 2, 128 RoI proposals, T4 GPU
- Loss: `L(total) = L(RPN-cls) + L(RPN-box) + L(ROI-cls) + L(ROI-box) + L(mask)`

**5. Post-Segmentation Processing**
- Bounding boxes removed
- RGB mask converted to binary
- Morphological operations applied
- Otsu thresholding
- Connected Component Analysis (CCA)
- Noise filtering (area < 2000 pixels removed)

**6. Midpoint & Axis Construction**
- Minimum-area rectangle fitted per tooth
- Top & bottom midpoints computed
- Vertical tooth axis generated

**7. Reference Line Generation**
- Maxillary teeth: Orbitale-to-orbitale line
- Mandibular teeth: Mental foramen-to-foramen line
- Dentist selects reference points via interactive tool

**8. Axial Inclination Calculation**
- Determinant-based line intersection formula
- Angle computed using vector dot-product method

**9. Statistical Validation**
- Compared AI-derived angles with manual dentist measurements
- Tests: Shapiro–Wilk, Levene's test, Unpaired t-test (p < 0.05)

### Model Accuracy

| Metric | Value |
|---|---|
| Precision | 0.83 |
| Recall | 0.92 |
| Dice Coefficient | 0.87 |
| IoU | 0.77 |

- 5-fold cross-validation performed
- Evaluated at pixel-level and object-level

### Key Outcomes
- Reliable instance-level segmentation
- Accurate mesiodistal axial inclination measurement
- Faster than manual (manual: 10–12 min/OPG)
- Clinically viable and scalable with limited GPU resources

---

## 2. Multiclass Segmentation using Teeth Attention Modules for Dental X-ray Images

### Methodology

Proposes a multiclass tooth segmentation architecture integrating:
- M-Net-like U-Net structure
- Swin Transformer
- Teeth Attention Block (TAB) — Novel Contribution
- Multiscale Supervision
- Squared Dice Loss

### Architecture

**Encoder–Decoder (U-Net/M-Net-like)**
- 3×3 convolution layers, Batch Normalization, ReLU
- Max-pooling for downsampling, transposed convolution for upsampling
- Skip connections between encoder and decoder

**Swin Transformer (at bottleneck)**
- Captures long-range dependencies via window-based self-attention
- Handles global contextual information

**Teeth Attention Block (TAB) — Novel Component**
- Boundary-aware refinement filter
- Self-attention mechanism
- Reduces noise, enhances differentiation between adjacent/overlapping teeth
- Integrated into skip connections

### Preprocessing
- Resize to 1024×512
- Normalize pixel intensities to [0, 255]
- Multiscale morphology operations, noise reduction, contrast enhancement

### Loss Function

Squared Dice Loss: `L = 1 − (2∑(yt·yp) + ε) / (∑(yt² + yp²) + ε)`

Handles class imbalance and gives more weight to boundary pixels.

### Dataset
- 540 panoramic dental X-ray images
- 32 tooth classes (FDI notation: #11–#18, #21–#28, #31–#38, #41–#48)
- Split: 70% training / 15% validation / 15% testing

### Results

| Metric | Proposed Model |
|---|---|
| Accuracy (ACC) | 0.9726 |
| Dice (DSC) | 0.9102 |
| Jaccard Index (JI) | 0.8501 |
| Precision | 0.8046 |
| Recall | 0.9389 |
| Specificity | 0.9730 |

### Ablation Study

| Variation | DSC |
|---|---|
| Basic U-Net | 0.7602 |
| + Deep Supervision | 0.7846 |
| + Swin Transformer | 0.7644 |
| + TAB | 0.9001 |
| **Full Proposed Model** | **0.9102** |

Biggest improvement came from TAB.

### Key Contributions
- First architecture combining CNN (U-Net), Swin Transformer, and TAB
- Boundary-aware attention for precise tooth segmentation
- Segmentation of 32 tooth classes
- Training time: ~60 minutes (RTX 3090)

---

## 3. Boundary Feature Fusion Network for Tooth Image Segmentation

### Methodology

Proposes **BFFNet** (Boundary Feature Fusion Network) to solve blurred tooth boundaries in panoramic X-rays.

**Main Components:**

- **ResNet Backbone** — Extracts multi-level features (low-level + high-level)
- **Boundary Feature Extraction Module (BFEM)** — Uses reverse attention mechanism; enhances fine boundary details
- **Feature Cross-Fusion Module (FCFM)** — Fuses boundary details with global semantic features using local attention
- **Loss Function** — Weighted IOU Loss + Weighted BCE Loss with deep supervision

### Dataset & Results

- Dataset: STS (MICCAI 2023 Challenge), 2000 panoramic dental images

| Metric | BFFNet |
|---|---|
| Dice | 0.7911 |
| IOU | 0.9848 |
| Hausdorff Distance | 0.0174 |
| Overall Score | 0.9061 |

BFFNet outperformed U-Net, U-Net++, LDNet, and CCBANet.

---

## 4. Integrated Segmentation and Detection Models for Dentex Challenge 2023

*Lanshan He, Yusheng Liu, Lisheng Wang — Shanghai Jiao Tong University*

### Objective

Detect abnormal teeth from panoramic dental X-rays, predict disease labels, and predict enumeration IDs (FDI notation) for the Dentex Challenge 2023.

### Pipeline

1. **Tooth Detection**
2. **Disease Detection**
3. **Label Matching**

Tooth detection and disease detection are solved separately, then merged.

### Dataset

- **Subset 1:** Quadrant labels
- **Subset 2:** Tooth labels (quadrant + enumeration ID → global enumeration ID 1–32)
- **Subset 3:** Disease labels (quadrant + enumeration + disease ID)

Annotations converted to COCO and YOLO formats. Segmentation images resized to 256×256.

### Tooth Detection

**Detection Model:** DINO (DETR-based), backbone ResNet-50, pretrained on COCO

**Segmentation Models:** U-Net, SE U-Net (U-Net + Squeeze-and-Excitation)

Two strategies:
- *Whole Image Segmentation:* Train on full image, predict 32 classes
- *Quadrant-wise Segmentation:* Detect quadrants (DiffusionDet) → crop → predict 9 classes per quadrant

### Disease Detection

- **DINO** (Swin Transformer backbone): Pre-trained on tooth detection, fine-tuned on disease dataset
- **YOLOv8:** Trained directly on disease dataset
- **Ensembling:** Weighted Boxes Fusion (WBF) at inference

### Label Matching

IOU-based voting — each enumeration ID receives votes weighted by IOU; highest vote wins.

### Results

**Disease Detection Performance:**

| Model | AR | AP | AP50 | AP75 |
|---|---|---|---|---|
| DINO | 0.544 | 0.343 | 0.508 | 0.411 |
| YOLOv8 | 0.530 | 0.352 | 0.539 | 0.399 |
| **Fused** | **0.592** | **0.371** | **0.543** | **0.447** |

**Final Challenge Test Set:**

| Label Type | AR | AP | AP50 | AP75 |
|---|---|---|---|---|
| Quadrant | 0.753 | 0.474 | 0.679 | 0.585 |
| Enumeration | 0.681 | 0.353 | 0.511 | 0.421 |
| Disease | 0.592 | 0.371 | 0.543 | 0.447 |

### Limitations
- Enumeration AP relatively low (0.353)
- Heavy reliance on bounding box alignment
- Multi-stage pipeline increases complexity

---

## 5. A Deep Learning Approach to Teeth Segmentation and Orientation from Panoramic X-Rays

*Mou Deb, Madhab Deb, Mrinal Kanti Dhar*

### Objective

Two simultaneous tasks:
1. Teeth instance segmentation
2. Teeth orientation estimation

Proposes a two-stage framework: deep learning-based instance segmentation followed by PCA-based oriented bounding box (OBB) estimation.

### Dataset

- **DNS Dataset:** 543 images, resolution 1991×1127
- 5-fold split: 111 test images, 108 per other fold
- 32 tooth labels (FDI system)
- Patch size: 512×512, overlap: 10×10, stride: 502

### Architecture: Modified FUSegNet

- **Encoder:** EfficientNet-B7 (pretrained on ImageNet, compound scaling α=1.2, β=1.1, γ=1.15)
- **Decoder:** Upsampling + concatenation with attention-gated encoder features
- **Grid-Based Attention Gates:** Reduce false positives, focus on small tooth structures (~1.5% IoU improvement)
- **P-scSE Module:** Parallel channel SE + spatial SE with addition + maxout

### OBB via PCA

- No ground truth orientation available → PCA used
- Angle calculation:
  - If PCAangle < 0: θ = 180 + (90 − PCAangle)
  - Else: θ = (90 − PCAangle)

### Training
- Optimizer: Adam, LR: 0.001, weight decay: 1e-5, 50 epochs
- Loss: Dice Loss + Focal Loss

### Segmentation Results

| Model | IoU | DSC |
|---|---|---|
| DeepLabV3+ | 80.45 | 89.17 |
| FPN | 81.75 | 89.76 |
| FUSegNet | 80.79 | 89.38 |
| UNet | 67.93 | 80.90 |
| **Proposed** | **82.43** | **90.37** |

### OBB Results

| Metric | Value |
|---|---|
| RIoU | 82.82% |
| False Positives | 0 |

### Model Stats
- Parameters: ~66M
- Inference time: 1.2 seconds/image

---

## 6. Self-Supervised Learning with Masked Image Modeling for Teeth Numbering, Detection of Dental Restorations, and Instance Segmentation

*Amani Almalki, Longin Jan Latecki*

### Objective

Apply self-supervised learning (SSL) via Masked Image Modeling (MIM) to improve teeth numbering, detection, dental restoration detection, and instance segmentation. First work applying SimMIM and UM-MAE to Swin Transformer on dental panoramic X-rays.

### Dataset

- Base: DNS dataset (543 panoramic X-rays, 1991×1127)
- Enhanced to **TNDRS dataset**: fixed overlapping instances, corrected annotations, added restoration segmentation (direct, indirect, root canal therapy)

### Methodology

**Stage 1 — Self-Supervised Pre-training:**
- Swin Transformer encoder
- SimMIM (mask ratio 20%, patch 16×16, L1 loss, 100 epochs)
- UM-MAE (mask ratio 25%, MSE loss, 800 epochs)

**Stage 2 — Downstream Tasks:**
- Backbone: Swin-B, Framework: Cascade Mask R-CNN, Neck: FPN

### Results — Before Restoration Augmentation

| Initialization | APbox | APmask |
|---|---|---|
| PANet (CNN) | 75.4 | 73.9 |
| Random Swin | 75.7 | 74.8 |
| Supervised Swin | 79.1 | 78.3 |
| UM-MAE | 84.5 | 83.2 |
| **SimMIM** | **86.1** | **84.6** |

### Results — After Adding Restorations

| Initialization | APbox | APmask |
|---|---|---|
| Random | 77.0 | 76.1 |
| Supervised | 80.3 | 79.2 |
| UM-MAE | 88.3 | 85.7 |
| **SimMIM** | **90.4** | **88.9** |

### Mask Ratio Effect

| Mask Ratio | APbox | APmask |
|---|---|---|
| 60% | 84.3 | 83.2 |
| 20% | **86.1** | **84.6** |
| 10% | 85.8 | 84.3 |

Lower mask ratio works better — dental features are small; high masking removes too much detail.

### Dataset Correction Impact

| Condition | APbox | APmask |
|---|---|---|
| Before correction | 80.2 | 78.2 |
| After correction | 86.1 | 84.6 |

### Efficiency

| Method | Time | Memory |
|---|---|---|
| SimMIM | 24.6h | 18.7 GB |
| UM-MAE | 12.5h | 6.7 GB |

### Key Findings
- SimMIM > UM-MAE in performance
- SSL > supervised initialization
- Dataset correction yields ~6% AP improvement
- Transformer + SSL outperforms CNN

---

## 7. S-R2F2U-Net: A Single-Stage Model for Teeth Segmentation

*Mrinal Kanti Dhar, Mou Deb*

### Objective

Three novel single-stage deep learning models for semantic teeth segmentation in panoramic dental X-rays, achieving high Dice score with reduced parameters.

### Dataset
- 1500 panoramic dental X-ray images, 10 categories
- Split: 911 training / 153 validation / 436 testing
- Patch size: 512×512, overlap: 10×10, normalized to [0,1]

### Architecture: Switch-Based U-Net

Five configurable switches:

| Switch | Function |
|---|---|
| SWC | Conv-BN-ReLU block |
| SWR | Recurrent block |
| SWRs | Residual connection |
| SWA | Attention gate |
| SWFD | Filter doubling |

### Proposed Models

| Model | Description | Params |
|---|---|---|
| S-R2U-Net | Recurrent at sL2, base filters {64,128,256,512,1024} | 77.17M |
| **S-R2F2U-Net** | Recurrent at sL2 + filter doubling, base filters {32,64,128,256,512} | **59.12M** |
| S-R2F2-Attn-U-Net | S-R2F2U-Net + attention | 59.25M |

### Loss Function

`L = λ1·L_CE + λ2·L_Dice` (best: λ1=1, λ2=0.5)

### Main Results

| Model | Dice | Params (M) |
|---|---|---|
| Attention U-Net | 92.55 | 43.94 |
| R2U-Net | 93.11 | 108.61 |
| ResUNet-a | 92.66 | 4.71 |
| **S-R2F2U-Net** | **93.26** | **59.12** |

### Final Performance

| Metric | Value |
|---|---|
| Accuracy | 97.31% |
| Specificity | 98.55% |
| Precision | 94.27% |
| Recall | 92.61% |
| Dice | 93.26% |

### Key Findings
- Reducing recurrent modules reduces parameters significantly
- Filter doubling compensates for performance loss
- Hybrid loss boosts Dice
- Attention adds minimal benefit

---

## 8. DE-KAN: A Kolmogorov Arnold Network with Dual Encoder for Accurate 2D Teeth Segmentation

### Objective

Proposes **DE-KAN** (Dual Encoder – Kolmogorov Arnold Network) for accurate 2D teeth segmentation, addressing overlapping teeth, irregular shapes, sharp edges, and low-contrast regions.

### Datasets
- **CDPR Dataset:** 1500 training / 500 testing images
- **HTL Dataset:** 598 images (cross-dataset evaluation)
- Input size: 320×320

### Architecture

**Dual Encoder:**
- *ResNet-18* — Processes augmented images, extracts global semantic features
- *Custom CNN* — 4 conv layers (64→512 channels), captures local textures and tooth edges

**Feature Merging:** `F_merged = F_ResNet(xa) + AdaptiveAvgPooling(F_CNN(xn))`

**Bottleneck (KAN blocks):** Based on Kolmogorov–Arnold Representation Theorem — learnable nonlinear activations, improved interpretability

**Decoder:** Bilinear upsampling + 2 conv layers per stage + 1×1 conv output

### Loss Function

`Loss = 0.5 × BCE + DiceLoss`

### Training
- Framework: PyTorch, GPU: NVIDIA L20
- Batch size: 32, Optimizer: SGD (momentum 0.9), LR: 1e-4, Epochs: 200
- Scheduler: Cosine Annealing

### Results — CDPR Dataset

| Model | mIoU | Dice | Accuracy | Recall |
|---|---|---|---|---|
| U-KAN | 86.50 | 91.79 | 95.95 | 92.20 |
| Teeth U-Net | 87.96 | 92.21 | 96.09 | 92.78 |
| YOLOv8 | 85.91 | 90.90 | 93.30 | 91.68 |
| **DE-KAN** | **94.5** | **97.10** | **98.91** | **97.36** |

### Results — HTL Dataset

| Model | mIoU | Dice |
|---|---|---|
| Teeth U-Net | 84.27 | 89.69 |
| **DE-KAN** | **89.45** | **94.39** |

### Ablation Study

| Variant | mIoU | Dice |
|---|---|---|
| No KAN | 53.34 | 68.56 |
| KAN + CNN | 64.74 | 78.31 |
| KAN + ResNet | 55.39 | 70.50 |
| **Full DE-KAN** | **94.5** | **97.1** |

Dual encoder + KAN are both necessary.

### Computational Analysis

| Model | GFLOPs | Params (M) | Latency (ms) |
|---|---|---|---|
| U-KAN | 16.44 | 25.36 | 37.82 |
| Teeth U-Net | 75.24 | 36.04 | 55.63 |
| **DE-KAN** | 164.42 | 32.73 | 59.05 |

Higher GFLOPs but practical latency (59ms/image).

---

## 9. Tooth Instance Segmentation on Panoramic Dental Radiographs Using U-Nets and Morphological Processing

*Selahattin Serdar Helli, Andaç Hamamcı — Düzce University (2022)*

### Objective

U-Net-based tooth instance segmentation combined with grayscale morphological post-processing to separate touching teeth and improve tooth counting accuracy.

### Dataset
- 116 panoramic dental X-rays (Noor Medical Imaging Center, Iran)
- Used: 105 images (complete edentulous cases excluded)
- Resolution: 2600–3138 × 1050–1380 px → resized to 512×512

**Two mask types:**
- *Full Mask:* All teeth labeled together
- *Split Mask:* Each tooth separated by narrow artificial gaps

### Architecture

Standard U-Net trained from scratch (no pretrained weights), with dropout rates from 0.15 → 0.5 → 0.1 across layers.

### Training
- Framework: Keras, Optimizer: Adam, LR: 0.001
- Epochs: 250, Batch size: 4, Loss: Binary Cross Entropy

### Post-Processing (Core Contribution)

Applied before binarization:
1. Resize output (Lanczos interpolation)
2. Grayscale opening (5×5 square element)
3. Sharpening filter
4. Grayscale erosion (twice)
5. Otsu thresholding
6. Connected component labeling (threshold: 2000 pixels)

### Experiments

| Experiment | Mask Type | Augmentation | Post-Processing |
|---|---|---|---|
| E1 | Full | No | No |
| E2 | Split | No | No |
| E3 | Split | H+V+Noise | No |
| E4 | Split | H+Noise only | No |
| E5 | Split | No | Yes |

### Results

| Experiment | Dice (%) |
|---|---|
| E1 | 94.5 ± 0.7 |
| E2 | 95.1 ± 0.5 |
| E3 | 95.2 ± 0.3 |
| **E4** | **95.4 ± 0.3** |
| E5 | 95.3 ± 0.6 |

**Key findings:**
- Split mask significantly improves performance (p = 0.002)
- Horizontal flip + noise is best augmentation; vertical flip slightly harms results (panoramic X-rays are not vertically symmetric)

### Tooth Counting Performance

| Condition | Mean Error |
|---|---|
| Without post-processing | 26.81% |
| With post-processing | **6.15%** |

Significant improvement (p = 0.002) — lowest tooth counting error reported in literature.

### Comparison with Literature

| Study | Dice / F1 |
|---|---|
| Mask R-CNN (Jader) | 88% F1 |
| TSASNet | 92.72% Dice |
| Koch (U-Net) | 93.4% Dice |
| **This Study** | **95.4% Dice** |

### Key Achievements
- Dice: 95.4% with only 105 training images
- Tooth count error reduced from 26.81% → 6.15%
- No pretrained weights required
- Computationally lightweight
