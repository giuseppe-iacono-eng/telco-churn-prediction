# 📉 Telco Churn Prediction 📈

**End-to-end machine learning project** predicting customer churn using the [IBM Telco dataset](https://www.kaggle.com/blastchar/telco-customer-churn).  
The goal: **help businesses identify customers at risk of leaving** so they can take proactive retention actions.

---

## 🚀 Project Overview
- ✅ Built a data pipeline in **Google Colab** (connected to Drive for reproducibility).  
- ✅ Conducted **Exploratory Data Analysis (EDA)** to clean data and understand churn drivers.  
- ✅ Trained and compared **two models**:  
  - 🔹 Logistic Regression → baseline, interpretable  
  - 🔹 XGBoost → boosted trees, nonlinear, flexible  
- ✅ Selected a **business-relevant threshold** prioritizing recall (catching churners).  
- ✅ Used **SHAP explainability** to highlight which features drive churn and why.  
- ✅ Deployed a lightweight `predict_one` function to score new customers.  

---

## 📊 Results
- **Dataset size:** 7,043 customers, 21 features  
- **Churn rate:** ~26.5%  

**Model ROC-AUC:**
- Logistic Regression → **0.842**  
- XGBoost → **0.832**

**Business Threshold (recall ≥ 0.80):**
- Recall: ~82% ✅  
- Precision: ~50% ⚖️  
- Interpretation: out of 10 customers flagged, ~5 actually churn (good tradeoff if saving a customer is worth more than the retention cost).  

---

## 🔑 Key Insights
- 📌 Customers with **short tenure** are much more likely to churn.  
- 📌 **Month-to-month contracts** have highest churn risk.  
- 📌 **Higher monthly charges** and **fiber internet users** show higher churn tendency.  

💡 **Retention Strategy:**  
Focus retention offers on **new, high-charge, month-to-month customers**.

---

## 🖥️ Example Predictions
```python
# Risky customer
predict_one({"Contract":"Month-to-month", "tenure":3, "MonthlyCharges":95})
# → 0.83 churn probability

# Loyal customer
predict_one({"Contract":"Two year", "tenure":48, "MonthlyCharges":55})
# → 0.08 churn probability

