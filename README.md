---
title: SantanderTransactionClassifcation
emoji: 🏦
colorFrom: red
colorTo: red
sdk: streamlit
app_file: src/streamlit_app.py
pinned: false
short_description: Predict customer transaction probability with a LightGBM.
license: mit
---

# 🏦 Santander Customer Transaction Prediction (LightGBM)

This project predicts the probability that a customer will make a specific transaction in the future.
It is based on the Kaggle competition **Santander Customer Transaction Prediction**.

## ✅ Model
We trained and compared multiple models using ROC-AUC (main metric due to class imbalance):

- Logistic Regression: ROC-AUC ≈ **0.86**
- LightGBM (Final): ROC-AUC = **0.8888**
- XGBoost: ROC-AUC ≈ **0.8807**

LightGBM achieved the best ROC-AUC and was selected as the final model.

## 📁 Project Files
- `app.py` : Streamlit application
- `lightgbm_santander_model.pkl` : saved LightGBM model (joblib)
- `requirements.txt` : dependencies

> Important: Put `lightgbm_santander_model.pkl` in the same folder as `app.py`.

## 🚀 How to Run Locally
```bash
pip install -r requirements.txt
streamlit run app.py
🧪 How to Use the App
Upload a CSV file (e.g., Kaggle test.csv) containing:

ID_code

var_0 ... var_199

The app outputs:

probability (0–1)

predicted label (based on a threshold slider)

Download:

predictions_lightgbm.csv (probability + label)

submission_lightgbm.csv (Kaggle submission format: ID_code, target)

📌 Notes
Kaggle evaluation uses probabilities (ROC-AUC). Do not apply a threshold for Kaggle submissions.

The threshold in the app is only for display (label).

Due to platform limits, large Kaggle test files are processed locally. This app demonstrates the deployed model on compatible CSV samples.