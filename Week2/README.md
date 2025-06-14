# 🌿 NDVI-Based Land Cover Classification using Logistic Regression

This repository contains a complete machine learning pipeline to classify land cover types based on NDVI (Normalized Difference Vegetation Index) time series data. The model uses **Logistic Regression** with extensive feature engineering, dimensionality reduction, and preprocessing techniques.

---

## 📁 Files

- `ndvi_landcover_classification_logreg.ipynb` – Jupyter Notebook containing the full pipeline and model
- `hacktrain.csv` – Training dataset (with noisy NDVI features)
- `hacktest.csv` – Test dataset for final predictions
- `ndvi_submission_final.csv` – Final predictions in submission format

---

## 🧠 Features Engineered

The code extracts and processes the NDVI time series data with the following techniques:

### 🔹 Base Features
- Mean, Standard Deviation, Min, Max, Median, Range
- Skewness of NDVI values
- NDVI temporal trend

### 🔹 Seasonal Features
- Grouped NDVI values by seasons (Spring, Summer, Monsoon, Autumn, Winter)
- Seasonal mean and standard deviation

### 🔹 Temporal Difference & Trend Features
- First-order difference across NDVI time steps
- Mean and standard deviation of those differences

### 🔹 Smoothing Features
- 3-point moving average and moving standard deviation

---

## ⚙️ Model Pipeline

1. **Preprocessing**
   - Removed unnamed columns
   - Dropped low-variance features
   - KNN imputation for missing values
   - Standard scaling

2. **Dimensionality Reduction**
   - PCA (retaining 95% variance)
   - Polynomial Feature Expansion (Degree = 2)

3. **Model**
   - Multinomial Logistic Regression
   - `solver='saga'`, `C=50`, `max_iter=3000`, `class_weight='balanced'`

4. **Evaluation**
   - Train/Validation split (80/20)
   - Accuracy on validation set
   - 5-fold Stratified Cross-Validation

---

## 📈 Results

- ✅ **Validation Accuracy:** ~*84.68%*
- ✅ **Cross-Validated Accuracy:** ~*84.XX%* (check console output)

---

## 📤 Submission

The final predictions on the test set are saved to:

```
ndvi_submission_final.csv
```

Format:
```csv
ID,class
test_001,Forest
test_002,Urban
...
```

---

## 🚀 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/your-username/ndvi-landcover-classification.git
cd ndvi-landcover-classification
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

<sub>If `requirements.txt` is missing, install:</sub>
```bash
pip install pandas numpy scikit-learn
```

### 3. Run the notebook
Open `ndvi_landcover_classification_logreg.ipynb` in Jupyter and run all cells.

---

## 🛠️ Requirements

- Python 3.7+
- pandas
- numpy
- scikit-learn
- jupyter (optional)

---

## 📌 Notes

- Data contains **noise** due to cloud interference in NDVI values.
- Only **Logistic Regression** was used as per problem constraints.
- Feature engineering significantly improved model performance.

---

## 📬 Contact

Feel free to open an [issue](https://github.com/your-username/ndvi-landcover-classification/issues) or contact the developer for questions or improvements.

---

> © 2025 – NDVI Classification Hackathon Project