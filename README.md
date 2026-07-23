# Automated Detection of Parkinson's Disease from Gait Patterns Using AI

Final Year Project  
Faculty of Information Science and Technology, Multimedia University (MMU)

**Author:** Nur Insyirah Iman Mohd Azman  
**Supervisor:** Tee Connie

---

## Project Overview

This project develops an AI-based framework for automated Parkinson's Disease (PD) detection using gait patterns extracted from Timed Up and Go (TUG) test videos.

The proposed system combines human pose estimation, gait feature engineering, feature selection, and deep learning to classify subjects into Parkinson's Disease and Non-Parkinson's groups.

The framework extracts skeletal keypoints using **AlphaPose**, derives gait-related biomechanical features, detects Freezing of Gait (FoG) patterns, and utilizes LSTM-based deep learning models for classification.

---

## Objectives

- Develop an automated gait analysis pipeline for Parkinson's Disease classification.
- Extract meaningful gait characteristics from video-based human movement data.
- Investigate the effectiveness of feature selection techniques for high-dimensional gait features.
- Evaluate different LSTM architectures for subject-level Parkinson's Disease detection.

---

## System Pipeline

The proposed pipeline consists of the following stages:

```

TUG Video Input
|
v
Human Pose Estimation
(AlphaPose + COCO-17 Keypoints)
|
v
Gait Cycle Extraction
(Ankle-based Peak Detection)
|
v
Feature Engineering
(23 Gait Features + Freezing Index)
|
v
Feature Selection
(Correlation Filtering / Sequential Backward Selection)
|
v
Deep Learning Classification
(LSTM-based Models)
|
v
Parkinson's Disease Prediction

```

---

## Key Contributions

### 1. Video-Based Pose Extraction
- Extracted human skeletal keypoints from TUG walking videos using AlphaPose.
- Utilized COCO-17 body keypoint format to represent human movement patterns.

### 2. Gait Feature Engineering
Extracted 24 gait-related features:

**Conventional Gait Features (23):**
- Step width
- Step length
- Spine inclination
- Center of Gravity displacement
- Joint movement patterns
- Temporal gait characteristics

**Freezing of Gait Feature:**
- Freezing Index (FI) calculated using Fast Fourier Transform (FFT)-based frequency analysis.

### 3. Feature Selection
Implemented multiple feature selection strategies:

- Full Feature Set
- Correlation-Based Redundancy Filtering
- Sequential Backward Selection (SBS)

These methods were applied to reduce redundant features and improve model efficiency.

### 4. Deep Learning Classification
Developed and compared four LSTM-based architectures:

- Baseline LSTM
- Bidirectional LSTM (BiLSTM)
- Simple Attention LSTM
- Multi-Head Attention LSTM

---

## Dataset

### Self-Collected Dataset

The self-collected dataset is publicly available on Kaggle:

Dataset:
https://www.kaggle.com/datasets/insyirahazman/parkinsons-disease-dataset

### Dataset Summary

- Total subjects: 40
  - 20 Parkinson's Disease subjects
  - 20 Non-Parkinson healthy controls

- Data collection:
  - Dual camera setup (front and side views)
  - 30 FPS
  - 1080p resolution
  - TUG protocol:
    - Sit
    - Stand
    - Walk 3 meters
    - Turn
    - Walk back
    - Sit

- Data format:
  - AlphaPose JSON output
  - COCO-17 keypoint coordinates
  - Confidence scores

> The dataset is provided for academic and research purposes only. Please cite this project when using the dataset.

---

## Technologies Used

### Programming & Data Processing
- Python
- NumPy
- Pandas
- SciPy

### Computer Vision
- AlphaPose
- COCO-17 Human Pose Estimation

### Machine Learning & Deep Learning
- TensorFlow / Keras
- Scikit-learn
- LSTM Networks

### Development Environment
- Jupyter Notebook
- Google Colab

---

## Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Validation Loss

Evaluation was performed using subject-level data splitting to prevent data leakage between training and testing samples.

---

## Source Code

Complete implementation:

GitHub Repository:
https://github.com/insyirahazman/FYP_Parkinson_Disease

---

## Acknowledgement
```
Special thanks to my supervisor, Tee Connie, for the guidance and support throughout this research project.
```
