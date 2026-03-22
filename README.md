# Patient Readmissions Prediction

This project uses a diabetic dataset to build a readmission risk model and output features for Tableau analysis.

The dataset can be downloaded at: https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008

The Tableau visualization for this project can be found at: https://public.tableau.com/app/profile/arewa.iyi8174/viz/ClinicalReadmissionRiskOptimizerDiabetes130-UShospitalsdatasetVisualization/Dashboard1?publish=yes
## 📂 Files
- `diabetic_data.csv` - original dataset
- `IDS_mapping.csv` - mapping for discharge and admission IDs
- `PatientReadmissions.ipynb` - preprocessing + modeling notebook
- `Healthcare_AI_Project_Data.csv` - output dataset with risk tiers for Tableau

## 🧠 Objective
Predict patient readmission within 30 days (`target = 1` for `<30`) using RandomForest and generate feature-based patient risk tiers.

## 🧹 Preprocessing steps
1. Load data.
2. Remove expired/hospice patients from target set using `IDS_mapping.csv`.
3. Drop high-null features (`max_glu_serum`, `A1Cresult`) and low-value columns (`weight`, `payer_code`, `medical_specialty`).
4. Convert `readmitted` to binary target (`<30` = 1, else 0).
5. `dropna()` for clean dataset.
6. Label encode categorical features before model training.

## 🚀 Modeling
- RandomForestClassifier (n_estimators=100)
- Feature importance extraction
- Keep top features, train on all rows with those features
- Generate readmission probability and risk tiers (`High/Medium/Low`)

## 🗂 Export
- Output `Healthcare_AI_Project_Data.csv` with chosen features + `Risk_Tier` + `target` for Tableau

## 🛠 Requirements
- Python 3.9+
- pandas
- numpy
- scikit-learn

## ▶️ Run
Open `PatientReadmissions.ipynb`, run all cells.

## 🧩 Notes
- `LabelEncoder` is used for categorical variables so the model accepts numeric arrays.
- A Pandas warning appears about `select_dtypes(include=['object'])` in pandas 2.x; this does not break the pipeline.
