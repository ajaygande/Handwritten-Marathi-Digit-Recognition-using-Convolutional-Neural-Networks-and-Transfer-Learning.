# 🔢 Handwritten Marathi Digit Recognition
### Using Convolutional Neural Networks and Transfer Learning

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.20.0-orange?logo=tensorflow)
![Accuracy](https://img.shields.io/badge/Accuracy-91%25-brightgreen)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📌 Overview

This project presents a deep learning system for recognizing handwritten **Marathi digits (० through ९)** using **MobileNetV2** as a pre-trained backbone combined with a custom classification head. Marathi, spoken by over 83 million people, uses the Devanagari script — yet automated recognition of its handwritten digits remains significantly underexplored.

The model is trained on 1,000 images across 10 digit classes using a **two-phase transfer learning strategy**, achieving a final validation accuracy of **91%** and a macro F1-score of **0.91** — with only 1,000 training images.

A research paper based on this project has been included in this repository.

---

## 🔢 Marathi Digits Reference

| Marathi | ० | १ | २ | ३ | ४ | ५ | ६ | ७ | ८ | ९ |
|---------|---|---|---|---|---|---|---|---|---|---|
| English | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |

---

## 📊 Key Results

| Metric | Value |
|--------|-------|
| Final Validation Accuracy | **91.00%** |
| Macro Average F1-Score | **0.91** |
| Phase 1 Best Accuracy | **93%** (Epoch 10) |
| Total Parameters | **2,423,242** |
| Trainable Parameters (Phase 1) | **165,258** |

**Best performing digits:** ४ (4) and ८ (8) — Perfect F1-score of 1.00

**Most challenging digit:** ६ (6) — F1-score of 0.75 due to structural similarity with २ and ३

---

## 🏗️ Model Architecture

The model uses **MobileNetV2** pre-trained on ImageNet as a feature extractor with a custom classification head.

| Component | Details |
|-----------|---------|
| Base Model | MobileNetV2 (ImageNet weights) |
| Input Shape | 224 × 224 × 3 |
| Global Average Pooling | Applied |
| Dense Layer | 128 units, ReLU activation |
| Dropout | 0.4 |
| Output Layer | 10 units, Softmax |
| Optimizer | Adam |
| Loss Function | Categorical Cross-Entropy |

### Two-Phase Training Strategy

**Phase 1 — Feature Extraction (Epochs 1–15)**
- MobileNetV2 backbone frozen
- Only classification head trained
- Learning rate: 0.001 | Batch size: 32
- Best validation accuracy: **93% at Epoch 10**

**Phase 2 — Selective Fine-Tuning (Epochs 16–20)**
- Top 30 backbone layers unfrozen
- Reduced learning rate: 0.0001
- Final validation accuracy: **91%**

---

## 📁 Dataset

- **Source:** Kaggle — Handwritten Marathi Digits Dataset
- **Total Images:** 1,000 (100 images per class)
- **Classes:** 10 (Marathi digits ० through ९)
- **Class Distribution:** Perfectly balanced
- **Train / Validation Split:** 800 / 200 (80% / 20%)

---

## ⚙️ Preprocessing Pipeline

All images go through the following 6-step pipeline before training:

1. **Resizing** — All images resized to 224×224 pixels (MobileNetV2 input requirement)
2. **Normalization** — Pixel values rescaled from [0, 255] to [0, 1]
3. **Color Conversion** — Grayscale images converted to 3-channel RGB
4. **Data Augmentation** *(training only)* — Random rotation (±20°), width/height shift (20%), horizontal flip, zoom (20%)
5. **Batch Processing** — Batch size of 32
6. **Label Encoding** — Class labels encoded as integers (0–9)

---

## 📂 Repository Structure

```
├── Handwritten_Marathi_Digits_CNN_Portfolio.ipynb   # Main notebook — model, training, evaluation
├── Research_Paper.docx                               # Published research paper
└── README.md                                         # Project documentation
```

---

## 🚀 How to Run

**1. Clone the repository**
```bash
git clone https://github.com/ajaygande/Handwritten-Marathi-Digit-Recognition-using-Convolutional-Neural-Networks-and-Transfer-Learning.
cd Handwritten-Marathi-Digit-Recognition-using-Convolutional-Neural-Networks-and-Transfer-Learning.
```

**2. Install required libraries**
```bash
pip install tensorflow numpy matplotlib scikit-learn seaborn
```

**3. Download the dataset**

Download the Handwritten Marathi Digits dataset from Kaggle and place it in the project directory.

**4. Run the notebook**

Open `Handwritten_Marathi_Digits_CNN_Portfolio.ipynb` in Jupyter Notebook or Google Colab and run all cells.

---

## 📦 Requirements

```
Python        >= 3.8
TensorFlow    == 2.20.0
NumPy
Matplotlib
Scikit-learn
Seaborn
```

---

## 📄 Research Paper

This project is accompanied by a research paper:

> **Handwritten Marathi Digit Recognition Using Convolutional Neural Networks and Transfer Learning**
> Ajay Sudhakar Gande
> Department of Information Technology, Dr. G.Y. Pathrikar College of Computer Science and Information Technology, Chhatrapati Sambhajinagar, Maharashtra, India
> Guide: Dr. Satish Sankaye, M.Sc., M.Phil., Ph.D.
> May 2026

The paper covers dataset description, preprocessing pipeline, model architecture, two-phase training strategy, per-class evaluation, and future work.

---

## 👤 Author

**Ajay Sudhakar Gande**
M.Sc. Data Science — Department of Information Technology
Dr. G.Y. Pathrikar College of Computer Science and Information Technology
Chhatrapati Sambhajinagar, Maharashtra, India

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://linkedin.com/in/ajay-gande-5a38b2273)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?logo=github)](https://github.com/ajaygande)
