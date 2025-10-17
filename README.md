# 🛰️ Satellite Image Segmentation using U-Net and Flask

This project performs **satellite image segmentation** using a **custom U-Net model** and a **Flask web interface** for inference.  
It was initially developed and tested in a **Kaggle Python environment**.

---

## 🚀 Features

- Loads and preprocesses multi-channel satellite `.tif` images  
- Handles missing data (`-9999` values) by replacing with per-image mean  
- Performs per-channel **min-max normalization**  
- Trains a **U-Net model** from scratch for segmentation  
- Supports **transfer learning** with **EfficientNetB0** as encoder  
- Evaluates model using **IoU, Precision, Recall, and F1-score**  
- Saves model and normalization parameters (`.h5`, `.npy`)  
- Provides a **Flask UI** for interactive predictions  

---

## 📦 Project Structure


```text
project/
│
├── Model/
│   ├── my_model.h5
│   ├── mins.npy
│   ├── maxs.npy
│
├── static/
│   ├── uploads/
│   ├── results/
│
├── templates/
│   ├── upload.html
│   ├── result.html
│
├── app.py
├── README.md
└── requirements.txt
```


---

## 🧠 Model Details

- **Architecture:** U-Net (with optional EfficientNetB0 encoder)
- **Input size:** 128×128×10 channels
- **Loss function:** Weighted Binary Cross-Entropy + Dice loss
- **Metrics:**
  - IoU
  - Precision
  - Recall
  - F1-score
- **Optimizer:** Adam (`lr=1e-4`)
- **Epochs:** 100
- **Batch size:** 8

---

## 📊 Example Output

| Input Image | Predicted Mask |
|--------------|----------------|
| 🛰️ Satellite patch | 🟦 Segmentation mask |

---

## 🌐 Flask App

Run the trained model locally with Flask

Then open http://localhost:5000

Upload a .tif image and view:

- RGB preview

- Predicted segmentation mask