# Image_Processing_With_Machine_Learning_Project

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-red)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)
![License](https://img.shields.io/badge/License-Academic-lightgrey)


# 🌫️ CSIDNet: Compact Single Image Dehazing Network

## 📌 Overview
CSIDNet (Compact Single Image Dehazing Network) is a lightweight deep learning model designed to remove haze from a single input image. Unlike traditional dehazing methods that rely on estimating atmospheric parameters, CSIDNet directly learns to reconstruct a clean image using a compact CNN architecture.

This project is developed as part of the **IPML (Image Processing with Machine Learning)** course at **IIT Guwahati**.

---

## 🚀 Key Highlights
- ✅ Lightweight model (only 3 convolutional layers)
- ✅ Works with small datasets (~200 images)
- ✅ Real-time capable (low computational cost)
- ✅ Uses prior-based feature augmentation
- ✅ Residual learning for better reconstruction

---

## 🧠 Problem Statement
Outdoor images often suffer from haze due to atmospheric scattering and absorption. This reduces visibility and affects applications like:
- Autonomous driving
- Surveillance systems
- Remote sensing

The goal is to recover the clean image from a single hazy input.

---

## 💻 Model Architecture

### 🔹 Input Features (5 Channels)
Instead of just RGB, the model uses:
- **R, G, B channels**
- **Dark Channel Prior (DCP)**
- **Illumination Channel (Y channel)**

Final input tensor:
[R, G, B, Idark, IY]

---

### 🔹 Architecture Pipeline
1. **Feature Extraction**
2. **Feature Fusion (Conv + BN + LeakyReLU)**
3. **Residual Learning**
4. **Image Reconstruction**

---

### 🔹 Core Components
- 3 Convolutional Layers
- Batch Normalization
- Leaky ReLU Activation
- Skip Connection (Residual Learning)
- Sigmoid Output Layer

---

### 🔹 Residual Learning Concept
Instead of predicting clean image directly:

R(x) = I(x) - J(x)

J(x) = I(x) - R(x)


This improves convergence and preserves fine details.

---

## 📊 Dataset

The model is trained and evaluated on the **RESIDE Dataset**, which includes:

- **OTS (Outdoor Training Set)** → Training
- **SOTS (Synthetic Objective Test Set)** → Testing
- **HSTS (Real-world images)** → Generalization

📌 Training was performed on a subset (~200 images) to demonstrate efficiency.

---

## 📈 Evaluation Metrics

### 1. PSNR (Peak Signal-to-Noise Ratio)
- Measures reconstruction quality
- Higher = Better

### 2. SSIM (Structural Similarity Index)
- Measures structural similarity between images
- Range: 0 to 1 (higher is better)

---

### 📊 Results Summary
| Method      | PSNR | SSIM | Speed |
|------------|------|------|-------|
| DCP        | 16.6 | 0.81 | High Time |
| AOD-Net    | 28.2 | 0.90 | Medium |
| **CSIDNet**| **29.1** | **0.88** | **Low Time** |

---

### 🔬 Ablation Study
| Features Used              | PSNR | SSIM |
|--------------------------|------|------|
| RGB only                 | 27.5 | 0.82 |
| RGB + Dark Channel       | 28.5 | 0.86 |
| RGB + Dark + Illumination| 29.1 | 0.88 |

---

## ⚙️ How to Run the Project

### 🔹 Step 1: Clone Repository
```bash
git clone <your-repo-link>
cd CSIDNet

```
---
### 🔹 Step 2: Install Dependency
```bash
pip install numpy opencv-python matplotlib torch torchvision scikit-image tqdm
```

--- 
### 🔹 Step 3: Run Notebook
```bash
jupyter notebook CSIDNet_Implementation.ipynb
```
