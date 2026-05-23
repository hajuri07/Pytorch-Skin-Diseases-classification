# 🔬 SkinSense AI — Skin Disease Classifier

A deep learning-powered web application that classifies **7 types of skin diseases** from dermoscopy images using transfer learning with EfficientNetB0, achieving **81% validation accuracy** on the HAM10000 dataset.

![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square&logo=python)
![PyTorch](https://img.shields.io/badge/PyTorch-2.x-EE4C2C?style=flat-square&logo=pytorch)
![Streamlit](https://img.shields.io/badge/Streamlit-App-FF4B4B?style=flat-square&logo=streamlit)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

---

## 🖼️ Demo

> Upload a skin lesion image → get instant AI-powered classification with confidence scores

![App Screenshot](assets/demo.png)

---

## 🏥 Supported Disease Classes

| Class | Full Name | Risk Level |
|-------|-----------|------------|
| `akiec` | Actinic Keratosis | Moderate |
| `bcc` | Basal Cell Carcinoma | High |
| `bkl` | Benign Keratosis | Low |
| `df` | Dermatofibroma | Low |
| `mel` | Melanoma | Critical |
| `nv` | Melanocytic Nevi | Low |
| `vasc` | Vascular Lesion | Low |

---

## 🧠 Model Architecture

- **Base Model:** EfficientNetB0 pretrained on ImageNet (transfer learning)
- **Feature Extractor:** Frozen pretrained layers (leverage ImageNet knowledge)
- **Custom Classifier:**
  ```
  Dropout(0.3) → Linear(1280→256) → ReLU → Dropout(0.2) → Linear(256→7)
  ```
- **Dataset:** HAM10000 (10,015 dermoscopy images, 7 classes)
- **Training:** 10 epochs, Adam optimizer, ReduceLROnPlateau scheduler
- **Val Accuracy:** 81.13%

---

## 📊 Results

| Metric | Score |
|--------|-------|
| Overall Accuracy | 81.13% |
| Macro F1-Score | 0.63 |
| Weighted F1-Score | 0.80 |
| Best Class (nv) | 0.92 F1 |

---

## 🛠️ Tech Stack

- **Deep Learning:** PyTorch, TorchVision
- **Model:** EfficientNetB0 (Transfer Learning)
- **Data Processing:** Pandas, PIL, NumPy
- **Visualization:** Matplotlib, Seaborn, Plotly
- **Web App:** Streamlit
- **Evaluation:** Scikit-learn (confusion matrix, classification report)

---

## 🚀 Run Locally

**1. Clone the repo**
```bash
git clone https://github.com/hajuri07/skin-disease-classifier
cd skin-disease-classifier
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Download the dataset**
- Download [HAM10000](https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000) from Kaggle
- Place images in `data/HAM10000_images/`
- Place `HAM10000_metadata.csv` in `data/`

**4. Train the model**
```bash
jupyter notebook notebooks/train.ipynb
```

**5. Run the app**
```bash
streamlit run app.py
```

---

## 📁 Project Structure

```
skin-disease-classifier/
├── data/
│   ├── HAM10000_images/        ← dataset images
│   └── HAM10000_metadata.csv   ← labels
├── notebooks/
│   └── train.ipynb             ← training + evaluation
├── assets/
│   └── demo.png                ← screenshot for README
├── app.py                      ← Streamlit web app
├── requirements.txt
└── README.md
```

---

## ⚕️ Disclaimer

This project is for **educational purposes only** and is not a substitute for professional medical diagnosis. Always consult a qualified dermatologist for any skin concerns.

---

## 👤 Author

**Hajuri Ibrahim**
- GitHub: [@hajuri07](https://github.com/hajuri07)
- LinkedIn: [ibrahimhajuri](https://linkedin.com/in/ibrahimhajuri)
