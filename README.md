# 🔐 Intrusion Detection System using Hybrid ML-DL Model

## 📌 Overview

This project implements a **Hybrid Intrusion Detection System (IDS)** designed to detect malicious or anomalous network/API behavior using a combination of:

* 🧠 **Autoencoder (Deep Learning)** for anomaly detection
* 🌲 **XGBoost Random Forest (XGBRFClassifier)** for classification

The system learns **normal traffic patterns** and identifies deviations that indicate potential intrusions or failures.

---

## ⚙️ System Architecture

```
Raw Network/API Data 
        ↓
Data Preprocessing & Cleaning
        ↓
Feature Scaling (StandardScaler)
        ↓
Autoencoder (Deep Feature Extraction)
        ↓
Reconstruction Error + Latent Features
        ↓
XGBRFClassifier
        ↓
Normal / Intrusion Prediction
```

---

## 🧠 Core Idea

* The **Autoencoder** is trained on normal patterns → learns compressed representation
* **Reconstruction error** increases for anomalous inputs
* **Latent features** capture hidden structure
* These are combined and passed to **XGBoost**, which performs final classification

---

## 🧪 Model Performance

### 📊 Test Metrics

* **ROC-AUC:** 0.988
* **Accuracy:** 96%

### 🔢 Confusion Matrix

```
[[448002   6263]
 [ 14841  96470]]
```

### 📋 Classification Report

| Class | Meaning   | Precision | Recall | F1-score |
| ----- | --------- | --------- | ------ | -------- |
| 0     | Normal    | 0.97      | 0.99   | 0.98     |
| 1     | Intrusion | 0.94      | 0.87   | 0.90     |

---

## 🔍 Pipeline Breakdown

### 🔹 Data Preprocessing

* Missing value handling
* Feature normalization using `StandardScaler`

### 🔹 Autoencoder

* Input → Encoder → Latent Space → Decoder
* Outputs:

  * Reconstruction error
  * Latent vector

### 🔹 Feature Engineering

Final hybrid feature vector:

```python
[reconstruction_error, latent_features]
```

### 🔹 XGBRFClassifier

* Handles non-linear patterns
* Robust to noisy data
* Performs final intrusion classification

---

## ⚠️ Challenges & Solutions

| Challenge                 | Solution                            |
| ------------------------- | ----------------------------------- |
| Memory issues (Colab)     | Batch processing + variable cleanup |
| Overfitting (ROC ≈ 0.999) | Proper validation split             |
| Class imbalance           | Evaluation using ROC-AUC & recall   |

---

## 📈 Key Insights

* Hybrid models significantly improve IDS performance
* Reconstruction error is a strong anomaly indicator
* Latent features enhance classification accuracy
* Balanced evaluation is critical in security systems

---

## 🛠️ Tech Stack

* Python 🐍
* PyTorch 🔥
* XGBoost 🌲
* Scikit-learn ⚙️
* NumPy & Pandas 📊

---

## 👨‍💻 Author

**Aditya Raj**

* GitHub: https://github.com/AdityaRaj1411
