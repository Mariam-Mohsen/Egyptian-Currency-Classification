# Egyptian Currency Classification with YOLOv8, ResNet50 & Custom CNN

A complete **system** for classifying Egyptian banknotes into 9 denominations using  
**YOLOv8 Classification**, **ResNet50 Transfer Learning**, and a **Custom CNN**.

---

## Overview

This project builds a full image-classification pipeline capable of identifying Egyptian currency notes.  
It includes dataset preprocessing, training three deep-learning models, evaluation, testing on custom images,  
and exporting the final YOLO model for deployment on mobile, desktop, or real-time applications.

---

## Key Features

### Multi-Model Training
Three models were trained and compared:

- **YOLOv8s-cls** — Best accuracy (100% top-1, top-5)  
- **ResNet50** — High performance with transfer learning  
- **Custom CNN** — Lightweight baseline model  

---



##  Preprocessing Pipeline

### Applied steps:
- Resize all images to **224×224**
- Maintain aspect ratio with padding
- Normalize pixel values
- Convert labels using one-hot encoding (for Keras models)
- YOLO built-in augmentations:  
  - Random flipping  
  - RandAugment  
  - Random erasing  

These steps improve generalization and model robustness.

---

##  Model Architectures

###  Custom CNN  
A small convolutional neural network built from scratch:  
- Conv → ReLU → MaxPool (x2)  
- Flatten  
- Dense layers with dropout  
- Softmax classifier  

Serves as a baseline.

###  ResNet50 (Transfer Learning)  
- Pretrained on ImageNet  
- Frozen convolutional base  
- Added classification head (Dense layers → Softmax)  
- Improves accuracy significantly with fewer epochs  

###  YOLOv8 Classification  
- Pretrained `yolov8s-cls.pt` model  
- Automatically adjusts classification head for 9 classes  
- Fast training, excellent results, ready for deployment  

YOLO handles data loading, augmentation, and training internally.

---

##  Training Details

| Model | Epochs | Accuracy | Notes |
|-------|--------|----------|-------|
| Custom CNN | 15–20 | ~84% | Good baseline |
| ResNet50 | 15–20 | ~92% | Much better generalization |
| YOLOv8s-cls | 20 | **100%** | Best performance |
