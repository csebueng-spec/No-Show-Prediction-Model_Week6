# No-Show-Prediction-Model_Week6
HealthConnect Clinic — No-Show Prediction Model
AnalystLab Africa Experience Lab | Data Science Track
Python Jupyter Status Track

Project Overview
HealthConnect Clinic is a fictional healthcare provider that manages appointment-based services. This project uses data and machine learning to predict patient no-shows — helping the clinic reduce missed appointments, optimise appointment slot usage, and direct patient support more effectively.

Project question: How can HealthConnect Clinic use data and AI to reduce missed appointments and improve the patient support experience?

This repository contains the Data Science track contribution to the HealthConnect Experience Lab project, covering exploratory data analysis, data preprocessing, feature engineering, baseline modelling, model improvement, error analysis, and cross-track integration.

Project Status
Week	Focus	Status
Week 4	Problem definition, resource review, solution planning	✅ Complete
Week 5	EDA, preprocessing, feature engineering, baseline model	✅ Complete
Week 6	Model improvement, error analysis, RF vs LR comparison	✅ Complete
Week 7	Threshold optimisation, hyperparameter tuning, final test set evaluation	🔄 Upcoming
Key Results
Week 6 — Model Comparison Summary
Metric	Logistic Regression (Week 5)	Random Forest (Week 6)
Recall	0.603	0.625 ✅
Precision	0.668	0.648
F1-Score	0.634	0.636 ✅
ROC-AUC	0.680	0.652
Confusion Matrix Comparison
Error Type	Logistic Regression	Random Forest
True Negatives	~295	275
False Positives	~151	171
False Negatives	~200	189 ← 11 fewer missed
True Positives	~304	315 ← 11 more caught
Candidate Model for Week 7
Random Forest — selected on the basis of higher Recall (0.625) and fewer missed no-shows, which is the clinically more valuable outcome in the HealthConnect use case.

Logistic Regression is retained for Week 7 threshold optimisation, as its higher ROC-AUC (0.680) may yield competitive results at an optimised decision threshold.

Top Predictive Features (Random Forest)
Rank	Feature	Importance
1	booking_lead_days	0.182
2	distance_to_clinic_km	0.135
3	age	0.125
4	waiting_time_minutes	0.114
5	previous_appointments	0.066
6	no_show_rate (engineered)	0.038
Repository Structure
healthconnect-no-show-prediction/
│
├── data/
│   ├── raw/
│   │   └── HealthConnect_Appointment_Data.csv        # Original dataset (read-only)
│   └── processed/
│       └── healthconnect_binary_processed.csv        # Preprocessed modelling dataset
│
├── notebooks/
│   ├── Week5_HealthConnect_DS_Baseline.ipynb         # Week 5 baseline notebook
│   └── Week6_HealthConnect_DS_ModelImprovement.ipynb # Week 6 RF & comparison notebook
│
├── reports/
│   ├── Week5_DS_Baseline_Report.md                   # Week 5 baseline modelling report
│   ├── Week5_Project_Summary.md                      # Week 5 project summary
│   ├── Week6_DS_ModelImprovement_Report.md           # Week 6 model improvement report
│   └── Week6_Project_Summary.md                      # Week 6 project summary
│
├── .gitignore
├── requirements.txt
└── README.md
Dataset
File: HealthConnect_Appointment_Data.csv

The dataset contains 5,000 fictional and anonymised appointment records with the following key fields:

Category	Columns
Patient demographics	patient_id, gender, age, age_group
Appointment details	appointment_id, appointment_type, appointment_day, appointment_time, appointment_date
Booking information	booking_date, booking_lead_days
Historical behaviour	previous_appointments, previous_no_shows
Reminder information	reminder_sent, reminder_channel
Logistical factors	distance_to_clinic_km, waiting_time_minutes
Target	appointment_outcome (Attended / No-Show / Cancelled)
Important: The original dataset must not be overwritten. All processed or derived files are saved separately under data/processed/.

Approach
Week 5 — Baseline
Excluded Cancelled records → binary modelling dataset: 4,737 records
Patient-level 70/20/10 train/validation/test split (prevents data leakage)
One-hot encoding and median imputation (fitted on training data only)
Engineered no_show_rate = previous_no_shows / previous_appointments
Logistic Regression baseline: F1 0.634 / ROC-AUC 0.680
Week 6 — Improvement & Validation
Applied StandardScaler to numerical features (fitted on training data only)
Trained Random Forest classifier (n_estimators=100, class_weight='balanced')
Conducted error analysis: FP/FN breakdown and interpretation
Extracted RF feature importance rankings
Compared LR vs RF across all metrics
Recommended Random Forest as candidate model for Week 7
Setup & Installation
Requirements
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
Install dependencies:

pip install -r requirements.txt
Running the Notebooks
Option A — Jupyter Notebook:

# Week 5 baseline
jupyter notebook notebooks/Week5_HealthConnect_DS_Baseline.ipynb

# Week 6 model improvement
jupyter notebook notebooks/Week6_HealthConnect_DS_ModelImprovement.ipynb
Option B — Google Colab: Upload notebooks and dataset to Google Drive, then open via Google Colab.

Ensure the dataset path is updated:

df = pd.read_csv('path/to/HealthConnect_Appointment_Data.csv')
Tech Stack
Tool	Purpose
Python 3.10+	Core programming language
Pandas	Data manipulation and analysis
NumPy	Numerical operations and feature engineering
Matplotlib / Seaborn	Data visualisation
Scikit-learn	Preprocessing, modelling, and evaluation
Jupyter Notebook / Google Colab	Interactive development environment
GitHub	Version control and project documentation
Week 7 Plan
Threshold optimisation — identify optimal decision threshold for RF and LR to maximise Recall
RF hyperparameter tuning — grid search over n_estimators, max_depth, min_samples_split
is_new_patient feature — implement and evaluate impact on model performance
Final test set evaluation — evaluate selected model on held-out test set for the first time
Model finalisation — select the single best model for the HealthConnect solution
The Week 6 benchmark (RF: F1 0.636 / ROC-AUC 0.652) is the minimum threshold any Week 7 model must exceed.

Limitations
Dataset is fictional — model patterns may not generalise to real clinic data
reminder_channel has 27.3% missing values — encoding approach documented but not fully resolved
New patients (previous_appointments = 0) assigned no_show_rate = 0 — is_new_patient flag proposed for Week 7
Default classification threshold (0.5) used throughout Weeks 5–6 — threshold optimisation reserved for Week 7
Test set is reserved and has not yet been evaluated
Project Resources
Resource	File
Appointment Dataset	HealthConnect_Appointment_Data.csv
Data Dictionary	HealthConnect_Data_Dictionary.xlsx
Clinic Knowledge Base	HealthConnect_Clinic_Knowledge_Base.docx
About This Project
This project is part of the AnalystLab Africa Experience Lab Internship Programme. HealthConnect Clinic and all associated data are entirely fictional and created for educational purposes.

Intern: Christina Nompomelelo Sebueng Track: Data Science Programme: AnalystLab Africa Experience Lab

#AnalystLabAfrica
