# ML-Project-Health-Insurance-Cost-Predictor  

## 📌 **Overview**  
Predicting health insurance premiums accurately is **crucial** for ensuring fair pricing. Our project leverages **machine learning** to estimate premium amounts based on factors like **age, BMI, smoking status, and medical history**.  

With **50,000 records**, we built a robust model and deployed it on **Streamlit Cloud** for real-time predictions.  

🔗 **Live App:** [Health Insurance Cost Predictor](https://ml-project-health-insurance-cost-predictor-rohesen.streamlit.app/)  

---

## 🛠 **Data Processing Steps**  

### 🔹 **Step 1: Data Loading**  
✔ Loaded **50,000 rows & 13 columns**.  
✔ Standardized column names (lowercase & replaced spaces with "_").  

### 🔹 **Step 2: Data Cleaning**  
✔ **Missing Values:**  
   - **Smoking Status:** 11 missing  
   - **Employment Status:** 2 missing  
   - **Income Level:** 13 missing  
   - Solution: **Dropped them** (since they were negligible).  

✔ **Duplicates:** None found.  
✔ **Negative Values:** Fixed in **number_of_dependants** using `abs()`.  

### 🔹 **Step 3: Exploratory Data Analysis (EDA)**  
📊 **Univariate Analysis** (Numerical Columns: `age`, `number_of_dependants`, `income_lakhs`, `annual_premium_amount`)  
✔ **Outliers in Age:** Found unrealistic values (`max age = 350`), **removed** them.  
✔ **Outliers in Income:** Used **quantile method** (`0.999`), removed **10 rows**.  

📊 **Categorical Data Cleaning**  
✔ **Smoking Status Categories:** Merged inconsistent values into:  
   - ✅ `"No Smoking"` (Merged: `"No Smoking"`, `"Smoking=0"`, `"Does Not Smoke"`, `"Not Smoking"`)  
   - ✅ `"Regular"`  
   - ✅ `"Occasional"`  

### 🔹 **Step 4: Feature Engineering**  
✔ **Risk Score Calculation** from `medical_history`.  
✔ **Categorical Encoding:**  
   - **One-hot encoding:** `['gender', 'region', 'marital_status', 'bmi_category', 'smoking_status', 'employment_status']`  
   - **Ordinal encoding:** `['income_level', 'insurance_plan']`  

✔ **Feature Selection:** Removed non-essential columns:  
   ```python
   df4 = df3.drop(['medical_history', 'disease1', 'disease2', 'total_risk_score'], axis=1)
   ```  

### 🔹 **Step 5: Feature Scaling & Multicollinearity Check**  
✔ Used **Variance Inflation Factor (VIF)**:  
   - **Dropped `income_level`** (`VIF > 12`).  
   - After removal, **all VIF values < 10** ✅.  

### 🔹 **Step 6: Model Training**  
📈 **Models Used:**  
✔ **Linear Regression** → **92.8% Accuracy**  
✔ **XGBoost Regression** → **98% Accuracy** ✅  

### 🔹 **Step 7: Error Analysis**  
⚠ **Issue Found:**  
- **30% extreme errors** → Model **overcharges/undercharges by >10%** for these cases.  
- **46% error on one records of test predictions** → Something **wrong** in our model.  

🔎 **Root Cause Analysis:**  
- **Age ≤ 25** was causing inconsistencies in predictions.  
- **Needed more data on young individuals.**  

### 🔹 **Step 8: Data Segmentation & Model Refinement**  
✔ Requested additional data for **young individuals** → Received **"Genetic Risk" feature**.  
✔ **Segmented data into two datasets:**  
   1. **Young (age ≤ 25)**  
   2. **Rest of the population**  

📈 **Trained two separate models** → Achieved **98% accuracy** on both! 🎯  

---

## 🚀 **Deployment**  
✔ **Streamlit Cloud** for real-time predictions.  
✔ **Files hosted on GitHub** for seamless updates.  

🔗 **Live App:** [Health Insurance Cost Predictor](https://ml-project-health-insurance-cost-predictor-rohesen.streamlit.app/)  

---

## 📌 **Tech Stack**  
🚀 **Python** | 📊 **Pandas** | 📈 **XGBoost** | 🎨 **Streamlit** | ☁ **Cloud Deployment**  

---

## 📅 **Project Workflow**  

| **Step** | **Action** |  
|----------|-----------|  
| 🗂 **Data Loading** | Standardized column names ✅ |  
| 🧹 **Data Cleaning** | Fixed missing values & negative numbers ✅ |  
| 📊 **EDA** | Detected & removed outliers ✅ |  
| 🎯 **Feature Engineering** | Encoded categorical variables ✅ |  
| 📉 **Feature Selection** | Removed redundant columns ✅ |  
| 🤖 **Model Training** | Used **XGBoost (98% accuracy)** ✅ |  
| 🛠 **Error Analysis** | Identified age-related inconsistencies ✅ |  
| 🔍 **Model Refinement** | Created separate models for **young individuals** ✅ |  
| 🚀 **Deployment** | Live on **Streamlit Cloud** ✅ |  

---

## 🔄 **Next Steps**  
✔ Further optimize model performance 📈  
✔ Gather more **young individual** data for improved accuracy 🎯  
✔ Explore **deployment on AWS/GCP for scalability** ☁  

---

## 👥 **Team**  
- **📌 Project Lead:** Rohesen  
- **🛠 Data Engineer:** Rohesen 
- **📊 Machine Learning Engineer:** Rohesen 
- **📢 Deployment Specialist:** Rohesen  

---

## 💬 **Contact & Feedback**  
💡 Have suggestions? Found a bug? **Let’s improve together!**   

---

**🚀 Revolutionizing Insurance with AI!** 🏥💡  

Let me know if you need any modifications! 🚀🔥
