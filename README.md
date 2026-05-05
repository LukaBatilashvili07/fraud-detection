# fraud-detection
IEEE-CIS Fraud Detection მიზანია საბანკო ტრანზაქციებში თაღლითობის აღმოჩენა. შეფასების მეტრიკა - ROC-AUC.

## მიდგომა
გამოვიყენე რამდენიმე მოდელი, შევადარე მათი შედეგები და საუკეთესო მოდელი - MLflow Model Registry-ში.

## სტრუქტურა
- model_experiment_LogisticRegression.ipynb - Logistic Regression ექსპერიმენტი (+ L1, L2)
- model_experiment_DecisionTree.ipynb - Decision Tree ექსპერიმენტი (+ max depth = 5, 10)
- model_experiment_RandomForest.ipynb - Random Forest ექსპერიმენტი (n_estimators = 50, 100)
- model_experiment_AdaBoost.ipynb - AdaBoost ექსპერიმენტი (n_estimators = 50, 100)
- model_experiment_XGBoost.ipynb - XGBoost ექსპერიმენტი (+ RandomizedSearch)
- model_inference.ipynb - საუკეთესო მოდელის გამოყენება test set-ზე და submission ფაილის შექმნა
- README.md

## Feature Engineering

### კატეგორიული ცვლადების რიცხვითში გადაყვანა
კატეგორიული სვეტების დამუშავება - LabelEncoder.

### NaN მნიშვნელობების დამუშავება
- სვეტების წაშლა რომლებსაც >50% missing value ჰქონდა
- დარჩენილი სვეტების NaN-ების შევსება მედიანით

### ახალი Feature-ები
- amt_log
- amt_cents

## Cleaning მიდგომები
- '>50% missing value'-ს მქონე სვეტების წაშლა
- კატეგორიული ცვლადების LabelEncoding
- NaN-ების მედიანით შევსება

## Feature Selection

### გამოყენებული მიდგომები და შერჩევა
SelectKBest

## Training

### მოდელები
მოდელი - Train AUC , Val AUC 

Logistic Regression - 0.7184, 0.7257
Logistic Regression(L1) - 0.716371, 0.722896
Logistic Regression(L2) - 0.716371, 0.722896 
Decision Tree - 0.7768, 0.7313  
Decision Tree(Max Depth 5) - 0.7050, 0.7091
Decision Tree(Max Depth 10) - 0.7370, 0.7357 
Random Forest (50 trees) - 0.7722, 0.7568
Random Forest (100 trees) - 0.7725, 0.7583
AdaBoost(50 estimators) - 0.7136, 0.7186
AdaBoost(100 estimators) - 0.7178, 0.7234
XGBoost(Baseline) - 0.7468, 0.7509
XGBoost(RandomizedSearch) - 0.7574, 0.7584

### საბოლოო მოდელის შერჩევა
საუკეთესო მოდელი - XGBoost RandomizedSearch

### MLflow ექსპერიმენტების ბმული
https://dagshub.com/LukaBatilashvili07/fraud-detection.mlflow

## Kaggle score
- Kaggle score - 0.7989