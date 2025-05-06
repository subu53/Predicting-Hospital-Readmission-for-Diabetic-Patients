# Predicting Hospital Readmission for Diabetic Patients

**Repository:** [(https://github.com/subu53/Predicting-Hospital-Readmission-for-Diabetic-Patients)]

## 🏥 Project Description  
Predict 30-day hospital readmission risk for diabetic patients using clinical data from 130 US hospitals (1999-2008). This machine learning project aims to:  
✅ Identify high-risk patients for targeted interventions  
✅ Reduce healthcare costs and improve patient outcomes  
✅ Demonstrate end-to-end data science workflow for imbalanced classification  

**Dataset:** Contains 100,000+ patient records with:  
- Demographics  
- Encounter details  
- Diagnoses (ICD-9 codes)  
- Medications  
- Lab results  
- Prior hospitalization history  

---

## 🚨 Key Challenges Addressed  
- **Severe Class Imbalance** - Target variable (`readmitted_within_30_days`) represents <12% of data  
- **High Cardinality Features** - Multiple categorical features with 700+ unique values  
- **Data Quality** - Missing values (`?`), inconsistent formatting, and sparse features  

---

## 🎯 Project Objectives  
1. Build preprocessing pipeline for healthcare data  
2. Engineer features to capture clinical patterns  
3. Develop models optimized for imbalanced data  
4. Evaluate using F1-score, Recall, and ROC AUC  
5. Identify actionable risk factors for hospitals  

---

## 🛠️ Key Steps  

### Data Preparation  
- Replaced/Dropped missing values (`?`)  
- Removed identifiers (`encounter_id`, `patient_nbr`)  
- Grouped rare categories in:  
  - `medical_specialty` (11 categories)  
  - `discharge_disposition_id` (9 categories)  
  - Diagnosis codes (`diag_1/2/3`)  

### Feature Engineering  
- Created aggregate features:  
  - `num_active_meds`: Count of active medications  
  - `total_prior_visits`: Sum of historical visits  
  - `has_inpatient_prior`: Binary inpatient history flag  
- Encoded: `age` bins to numerical values  

### Modeling  
| Model                | Class Handling         | Best Metric           |
|----------------------|------------------------|-----------------------|
| Logistic Regression  | Class weights          | Recall = 0.60         |
| LightGBM             | Scale_pos_weight = 7.96| F1-score = 0.28       | 
| Random Forest        | Class weights          | ROC AUC = 0.676       |

---

## 📈 Results Summary  
**Top Performing Model (LightGBM):**  
- **Recall**: 49% of readmitted patients identified  
- **Precision**: 19% of flagged patients truly high-risk  
- **Key Predictors**:  
  1. Number of active medications  
  2. Patient age  
  3. Prior inpatient visits  

---

## 🔮 Future Work  
- Hyperparameter tuning with Bayesian optimization  
- Implement XGBoost/CatBoost comparisons  
- Test advanced resampling (ADASYN, SMOTE-ENN)  
- Develop SHAP-based explainability dashboard  
- Create API for real-time predictions  

---

## 📂 Repository Structure  
├── data/ # Raw datasets (diabetic_data.csv)
│ ├── predicting hospital readmission.ipynb
├── Predicting Hospital Readmission report
├── requirements.txt # Python dependencies
└── README.md # Project documentation


---

## 💡 Key Insights for Hospitals  
- **Priority Patients**: Elderly (70+) with 5+ medications  
- **Critical Window**: First 7 days post-discharge monitoring  
- **Prevention Strategy**: Medication reconciliation + early follow-ups  

---

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)  
*Contributions welcome! See CONTRIBUTING.md for guidelines.*
