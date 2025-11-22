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
- **ClinicalTrials.gov API** – study design, participant info, outcomes  
- **Attrition dataset** – dropout percentages for 1,325 trials  
- **RUCA Codes** – classify ZIP codes into rural vs. urban  

---

## Methods  

### 1. Data Retrieval & Integration  
- Retrieved JSON records for thousands of variables using the ClinicalTrials.gov API  
- Joined API data with attrition percentages  
- Merged trial ZIP codes with RUCA classifications  

### 2. Feature Engineering  
Engineered **23 features** across four categories:  
- Participant characteristics  
- Study design  
- Timeline and location  
- Serious adverse events  

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

Top predictors included:  
- Trial duration  
- Number of locations  
- Serious adverse events  
- Enrollment size  

### 4. Geospatial Analysis  
Developed an interactive map to visualize:  
- Trial facility locations  
- Urban vs. rural regions  
- Dropout percentages  

This highlighted spatial patterns in retention.

---

## Repository Structure  

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
└── README.md

---

## How to Run  
1. Clone the repository:  
   ```bash
   git clone https://github.com/felfeituri/clinical-trial-attrition-prediction.git
   cd clinical-trial-attrition-prediction
