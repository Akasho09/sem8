# 
1. FUSegNet
- deep learning framework called `FUSegNet`.
    - `EfficientNet-B4` encoder with attention mechanisms.
> CNN (Convolutional Neural Network) is a deep learning model used for image processing and feature extraction.

2. Dataset :
-  150 panoramic dental X-ray images from SaralPixel AI Labs.
Training: 120 images
Validation: 15 images
Testing: 15 images
- How many classes are there in your model?
    - 33 classes:
    32 tooth classes
    1 background class

3. Grid Attention :
- helps the model focus on important tooth regions while ignoring background information.
- To improve localization and separation of nearby teeth.

> scSE stands for Spatial and Channel Squeeze-and-Excitation.
- It improves feature refinement by focusing on important spatial and channel information.
- Grid Attention:
    -  Focuses on important regions
- scSE:
    - Refines important features

4. What preprocessing steps did you apply?
- Resizing
- Padding
- Normalization
- Augmentation 
    Rotation
    Translation
    Scaling
    Brightness adjustment
    Gaussian noise
    Gaussian blur


5. What loss function did you use?
- Hybrid loss:
    Focal Loss
    Dice Loss
    False Negative penalty
    Edge Loss
    Class Separation Loss

6. Which optimizer did you use?
- Adam optimizer.

- Learning rate?
    - 3 × 10⁻⁵
- Batch size?
    - 2
- Number of epochs?
    - 200
- What scheduler was used?
    - ReduceLROnPlateau.

7. What metrics did you use?
- Dice Score
    - Measures overlap between predicted and actual masks.
    > DSC=2TP/2TP+FP+FN
- IoU
    - Measures intersection divided by union.
    > IoU= TP/TP+FP+FN
- Precision
- Recall
- Tooth numbering accuracy

- What results did your model achieve?
    Dice = 0.913
    IoU = 0.851
    Precision = 0.925
    Recall = 0.910
    Tooth numbering accuracy = 99.3%


