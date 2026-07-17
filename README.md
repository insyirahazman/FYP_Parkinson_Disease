# AUTOMATED DETECTION OF PARKINSON’S DISEASE FROM GAIT PATTERNS USING AI 

Final Year Project — Faculty of Information Science and Technology, Multimedia University

**Author:** Nur Insyirah Iman Mohd Azman
**Supervisor:** Tee Connie

---

## 1. Project Overview

This project presents a video-based deep learning framework for Parkinson's Disease (PD) classification using skeletal keypoints extracted from Timed Up and Go (TUG) test videos. The pipeline extracts 24 gait features (23 conventional gait descriptors + 1 Freezing of Gait Freezing Index) from AlphaPose-derived COCO-17 keypoints, applies three feature selection strategies, and classifies subjects using four LSTM-based architectures across three TUG segments (full, walking, turning).

**Pipeline stages:**
1. Pose estimation and keypoint extraction (AlphaPose, COCO-17 format)
2. Gait cycle extraction (ankle-based peak detection)
3. Conventional gait feature extraction (23 features)
4. Freezing of Gait (FoG) feature extraction — Freezing Index (FI) via FFT
5. Feature selection (Full / Correlation Filtering / Sequential Backward Selection)
6. Model training (Baseline LSTM, BiLSTM, Simple Attention LSTM, Multi-Head Attention LSTM)
7. Evaluation (self-collected test set + online dataset)

---

## 2. Source Code

The complete source code is available at:

**[GitHub — (https://github.com/insyirahazman/FYP_Parkinson_Disease)]**

---

## 3. Self-Collected Dataset

The self-collected dataset used for model training and validation is publicly hosted on Kaggle:

**Dataset link:** https://www.kaggle.com/datasets/insyirahazman/parkinsons-disease-dataset

**Dataset summary:**
- 40 balanced subjects used in this study (20 Parkinson's Disease patients, 20 Non-Parkinson healthy controls)
- Healthy control subjects sourced from the MMU Fall Risk Prediction (MMU-FRiP) dataset (21 non-faller subjects) plus 2 additional subjects recorded via smartphone
- Recordings captured via dual tripod-mounted cameras (front + side view), 30 fps, 1080p resolution (16:9), plus 2 subjects recorded via handheld iPhone 11 in default landscape mode
- TUG protocol: seated start → stand → walk 3 meters → turn → walk back → sit
- Data format: AlphaPose JSON output (per-frame COCO-17 keypoint coordinates and confidence scores)

**To download and use:**
1. Create a free Kaggle account at https://www.kaggle.com if you don't already have one.
2. Navigate to the dataset link above and click "Download" (or use the Kaggle API — see below).
3. Extract the downloaded archive into the `data/self_collected/` directory (create this folder if it does not exist).
4. Ensure the folder structure separates PD and NP subjects as per the original labelling convention (used to assign binary labels: 0 = NP, 1 = PD).

> **Note:** This dataset is provided for academic/research purposes only, in accordance with participant consent obtained during data collection. Please cite this FYP/associated paper if you use this dataset in your own work.

---

### 4. AlphaPose (Pose Estimation Tool)

AlphaPose is required for keypoint extraction from raw TUG videos and is **not included** in this repository — it must be installed separately.

- **Official repository:** https://github.com/MVIG-SJTU/AlphaPose
- **Installation guide:** Follow the official AlphaPose installation instructions at the link above, which includes setting up PyTorch, building AlphaPose from source, and downloading pretrained detection/pose models.
- **Note:** AlphaPose requires a compatible CUDA-enabled GPU for reasonable inference speed; CPU-only inference is possible but significantly slower.

> **If your Kaggle dataset already contains pre-extracted AlphaPose JSON keypoint files (rather than raw videos), this step can be skipped** — clarify this in your dataset description if applicable, since it changes what a user needs to install.
