# PAPER 1 
##  Pano-GAN – Deep Generative Model for Panoramic Dental Radiographs

### 🔹 Problem
- AI requires large labeled datasets.
- Dental radiographs are:
    - Hard to collect
    - Time-consuming to annotate
    - Restricted by privacy and ethics

### Solution Proposed
- Use Generative Adversarial Networks (GANs) to create synthetic dental radiographs.
- Helps solve:
    - Data scarcity
    - Privacy concerns
    - Educational training needs

### ⭐ 3. Methodology
- 🔹 Dataset
    - 2322 panoramic dental radiographs
    - Focused on dentoalveolar region
- Images:
    - Cropped
    - Resized
    - Converted to grayscale
    - Normalized

### 🔹 Model Architecture
1. ✔ Generator
- Converts noise → synthetic radiograph
- Uses:
    - Transposed convolution
    - Batch normalization
    - ReLU activation

2. ✔ Discriminator (Critic)
- Distinguishes real vs fake images
- Uses:
    - Convolution layers
    - Instance normalization
    - Leaky ReLU

### 🔹 Model Variations
- Four models tested:
| Model | Denoising | Critic Iterations |
| ----- | --------- | ----------------- |
| M1    | No        | 2                 |
| M2    | Yes       | 1                 |
| M3    | Yes       | 4                 |
| M4    | Yes       | 5                 |


### 🔹 Evaluation Methods
1. Objective Evaluation
- FID Score
    - The Fréchet inception distance (FID) is a metric used to assess the quality of images created by a generative model, like a generative adversarial network (GAN) or a diffusion model.
- Measures similarity between real and fake images
- Lower score = better

2. t-SNE Visualization
- Shows feature similarity between datasets

### Expert Evaluation
- Dentist scored images using:
    - Realism
    - Clarity
    - Tooth structure
    - Bone structure
    - Artifacts
    - Anatomical landmarks
- Score range: 1 (poor) – 5 (excellent)

### ⭐ 4. Results
- 🔹 Objective Results
- Generated images:
    - More realistic than random noise
    - Less realistic than real radiographs
- t-SNE showed:
    - Fake images closer to real images but still distinguishable

### 🔹 Expert Evaluation Results
- Model 1 best for:
    - Fine bone structures
- Model 2 best for:
    - Clarity
    - Overall realism
    - Bone shape
- 🔹 Key Observation
    - Denoising improves overall image clarity
    - Non-denoised data preserves fine details


### 🔹 Common Problems in Generated Images
- Artifacts
- Extra teeth rows
- Poor anatomical accuracy

### ⭐ 5. Discussion
1. 🔹 Achievements
- Demonstrated GAN potential in dental imaging
- Generated moderately realistic radiographs

2. 🔹 Limitations
- Small training dataset
- Lack of labeled anatomical data
- High computational requirements

3. 🔹 Future Improvements
- Larger multi-center datasets
- High-resolution generation techniques
- Diffusion models
- Segmentation-based image generation
- Customizable pathology simulation

### ⭐ 6. Conclusion
- ✔ WGAN-GP successfully generated synthetic panoramic radiographs
- ✔ Generated images showed partial anatomical realism
- ✔ Synthetic data can support:
    - AI model training
    - Dental education
- ⚠ Performance limited by:
    - Dataset size
    - Model complexity
    - Image realism challenges


### DATES :
Received: 25 November 2024
Revised: 16 January 2025
Accepted: 30 January 2025
Published: 2 February 2025

