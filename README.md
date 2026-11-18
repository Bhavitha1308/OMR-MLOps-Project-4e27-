# OMR-MLOps-Project-4e27-
# OMR MLOps Project – Predicting Rejected Answer Sheets

## 1. Project Overview
This project develops an MLOps system to predict whether an OMR (Optical Mark Recognition) answer sheet will be rejected during automated scanning.

The system identifies scanning problems and predicts whether the sheet should be accepted or sent for manual verification.

## 2. Objectives
- Generate synthetic OMR scanning datasets.
- Maintain different dataset versions.
- Perform data preprocessing and feature engineering.
- Train Logistic Regression and Random Forest models.
- Compare model performance.
- Track and register models using MLflow.
- Implement CI/CD using GitHub Actions.
- Deploy a prediction API using FastAPI.

## 3. Technologies Used
- Python
- Google Colab
- Pandas and NumPy
- Scikit-learn
- MLflow
- FastAPI
- Pytest
- GitHub Actions

## 4. Dataset Description

The synthetic dataset contains 300 OMR scanning records.

Input attributes:
- Scan Resolution (DPI)
- Sheet Rotation Angle
- Print Contrast Score
- Alignment Marker Visibility
- Multiple Marked Questions
- Blank Answer Percentage
- Sheet Damage Score
- Scanner Type

Target variable:
- `scan_rejected` (Yes/No)

### Dataset Versions
- Version 1: Normal scanning conditions.
- Version 2: Increased scanning misalignment and reduced print contrast.

## 5. Feature Engineering

Two new features are created:

1. **Scan Quality Index:** Measures the overall quality of the scanned OMR sheet.
2. **Marking Error Ratio:** Measures the marking error level.

The engineered features are stored in a reusable feature store CSV file.

## 6. Machine Learning Models

Two algorithms are trained:

- Logistic Regression
- Random Forest

Evaluation metrics:
- Accuracy
- Precision
- Recall
- F1-score

The model with better rejection-detection performance is selected.

## 7. MLflow Model Registry

MLflow is used for:
- Experiment tracking
- Parameter logging
- Metric logging
- Model registration

Registered model name: `OMR_Rejection_Model`

## 8. CI/CD Pipeline

GitHub Actions is used to automate testing.

The pipeline performs:
- Repository checkout
- Python environment setup
- Dependency installation
- Automated Pytest execution

## 9. Model Deployment

FastAPI is used to create a prediction API.

The API accepts OMR scanning information and returns:

- **Scan Accepted**
- **Manual Verification Required**

## 10. Project Structure

```text
OMR-MLOps-Project/
│
├── omr_version1.csv
├── omr_version2.csv
├── omr_feature_store.csv
├── omr_model.pkl
├── app.py
├── test_omr.py
├── requirements.txt
├── README.md
└── .github/
    └── workflows/
        └── omr-ci.yml
```

## 11. How to Run the Project

### Install dependencies

```bash
pip install -r requirements.txt
```

### Run FastAPI

```bash
uvicorn app:app --reload
```

### Open API documentation

```text
http://127.0.0.1:8000/docs
```

### Run automated tests

```bash
pytest -v
```

## 12. Conclusion

This project demonstrates a complete MLOps workflow for predicting rejected OMR answer sheets. It includes synthetic dataset creation, dataset versioning, feature engineering, machine learning, MLflow model registration, automated CI/CD testing and FastAPI model serving.

The system helps examination staff identify potentially rejected answer sheets and perform manual verification when required.

---
**Project:** OMR Rejection Prediction using MLOps  
**Development Platform:** Google Colab  
**Repository:** OMR-MLOps-Project
