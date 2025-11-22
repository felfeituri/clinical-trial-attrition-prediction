# Predicting Patients’ Attrition Percentage in Clinical Trials
### Leveraging Machine Learning and Geospatial Analysis to Understand Clinical Trial Retention  
*HIDS 6001 – Massive Health Data Fundamentals*  
*Project by Fadwa Elfeituri, Maxwell Lewis, Tsegie Kassahun*  

---

## Overview  
This project develops a machine-learning pipeline to predict patient attrition percentages in clinical trials and to analyze geographic retention patterns.  
We retrieved clinical study data from the **ClinicalTrials.gov API**, merged it with an attrition dataset of **1,325 trials**, engineered structured features, trained predictive models, and built an interactive geospatial visualization using RUCA classifications.

---

## Objectives  
- Predict patient attrition using machine learning techniques  
- Engineer structured features from clinical, demographic, and location variables  
- Identify the strongest predictors of dropout  
- Visualize geographic patterns across trial facilities  
- Highlight urban–rural differences in attrition rates  

---

## Data Sources  
- **Primary Dataset:** Attrition dataset (`ct_attrition_dataset.csv`) containing **1325 clinical trials** with **NCT numbers and attrition percentage**.  
- **Data Source:** [ClinicalTrials.gov API](https://clinicaltrials.gov/api/v2/studies/NCT04513925)  
- **Additional Data:** [Rural-Urban Commuting Area (RUCA) Codes](https://depts.washington.edu/uwruca/ruca-download.php)  

---

## Methods  

### 1. Data Retrieval & Integration  
- Retrieved JSON records for thousands of variables using the ClinicalTrials.gov API  
- Joined API data with attrition percentages  
- Merged trial ZIP codes with RUCA classifications  

## 2. Feature Engineering
Engineered **23 features** across four categories:  
- Participant characteristics  
- Study design  
- Timeline and location  
- Serious adverse events  

### Extracted from ClinicalTrials.gov API:  
- **Study Design:** Trial setup, phases, masking information  
- **Eligibility Criteria:** Demographics, mean age, gender ratio  
- **Recruitment Locations:** Hospitals/organizations where patients were recruited  
- **Therapy/Disease Information:** Drugs or treatments being studied  

### Engineered Features:  
- **Number of recruitment locations per trial**  
- **Clinical trial duration (start to completion date)**  
- **Trial phase (Phase 1, 2, 3, or 4)**  
- **Serious adverse events reported**  
- **RUCA classification (Urban vs. Rural trials)**  

Applied:  
- Median imputation  
- One-hot encoding  
- Custom feature creation (trial duration, condition count, arm group count)

### 3. Model Development  
Trained and compared two models:  
- **Random Forest Regressor**  
- **XGBoost Regressor** (best performer)

Performance:  
- XGBoost: **R² = 0.33**, RMSE = 8.67  
- Random Forest: **R² = 0.31**, RMSE = 8.79  

### Key Insights:  
- **Trial Duration** was the strongest predictor of attrition.  
- **Serious Adverse Events** increased dropout rates.  
- **Enrollment Size** correlated with attrition (larger trials had more dropouts).  
- **Geographic factors (locations)** impacted attrition, highlighting accessibility issues.  

### 4. Geospatial Analysis & Mapping Clinical Trials  
- Extracted facility locations (latitude, longitude) using:  
  - **ClinicalTrials.gov API**  
  - **Zip Code Database (`pyzipcode` package)**  
- **Mapping Tool:** `folium` for **interactive visualization**  
- **Color-coded density map** based on attrition rates  

---

## Repository Structure  
```
clinical-trial-attrition-prediction/
│
├── notebooks/
│   ├── ClinicalAttrition_FeatureEngineering_DataProcessing.ipynb
│   ├── ClinicalAttrition_Model.ipynb
│   └── ClinicalAttrition_Map.ipynb
│
├── report/
│   └── ClinicalAttrition_Report.pdf
│
├── presentation/
│   └── Clinical Attrition Project 3 - HIDS 6001.pptx
│
├── requirements.txt
└── README.md
```
---

## How to Run  
1. Clone the repository:  
   ```bash
   git clone https://github.com/felfeituri/clinical-trial-attrition-prediction.git
   cd clinical-trial-attrition-prediction
2. Install Requirements 
   ```
   pip install -r requirements.txt
   ```
3. Run notebooks in this order:
- ClinicalAttrition_FeatureEngineering_DataProcessing.ipynb
- ClinicalAttrition_Model.ipynb
- ClinicalAttrition_Map.ipynb

---

## Tools & Libraries

- Python
- Pandas, NumPy
- Scikit-learn
- XGBoost
- Requests (API retrieval)
- Plotly / Folium (mapping)
-Matplotlib, Seaborn

---

## Team

This project was developed as a group project for Georgetown University’s
HIDS 6001: Massive Health Data Fundamentals course.

Team members:
- Fadwa Elfeituri
- Maxwell Lewis
- Tsegie Kassahun
