# Heart Disease Classification Project - ML Assignment 2

This repository contains the complete machine learning classification project developed to predict the clinical presence of heart disease using patient data.

---

## a. Problem Statement
Cardiovascular diseases (CVDs) are the number one cause of death globally, taking an estimated 17.9 million lives each year. Early detection and automated classification of patients at high risk of heart disease can assist clinicians in executing timely therapeutic interventions. The goal of this project is to build and evaluate five distinct machine learning classification models to predict the presence of heart disease based on clinical features, selecting the most robust model for deployment.

---

## b. Dataset Description
* **Source**: UCI Heart Disease Dataset
* **Size**: 918 instances with 12 clinical attributes (7 numerical, 5 categorical).
* **Class Distribution**: Heart Disease (1): 55.34% | Normal (0): 44.66% (handled via stratified split to avoid bias).

### Attributes Detail:
1. **Age**: Age of the patient [years]
2. **Sex**: Gender [M: Male, F: Female]
3. **ChestPainType**: Chest pain type [TA: Typical Angina, ATA: Atypical Angina, NAP: Non-Anginal Pain, ASY: Asymptomatic]
4. **RestingBP**: Resting blood pressure [mm Hg]
5. **Cholesterol**: Serum cholesterol [mg/dl] (Zeros replaced as NaNs and imputed class-wise)
6. **FastingBS**: Fasting blood sugar [1: if FastingBS > 120 mg/dl, 0: otherwise]
7. **RestingECG**: Resting electrocardiogram results [Normal, ST: ST-T wave abnormality, LVH: Left Ventricular Hypertrophy]
8. **MaxHR**: Maximum heart rate achieved [Numeric value between 60 and 202]
9. **ExerciseAngina**: Exercise-induced angina [Y: Yes, N: No]
10. **Oldpeak**: ST depression induced by exercise relative to rest [Numeric value]
11. **ST_Slope**: The slope of the peak exercise ST segment [Up, Flat, Down]
12. **HeartDisease** [Target]: Output class [1: heart disease, 0: Normal]

---

## c. GitHub Repository Link
* **Project Repository**: [GitHub Link Placeholder - Replace with your repository URL]

---

## d. Models Used & Performance Comparison

We trained and tested 5 clinical classifiers on the fully cleaned, imputed, and scaled dataset. The comprehensive evaluation metrics for each model on the 20% test partition are shown in the comparative table below:

### Model Performance Metrics Table
| Model | Accuracy | AUC Score | Precision | Recall | F1 Score | MCC Score |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Logistic Regression** | 0.8913 | 0.9350 | 0.8942 | 0.9118 | 0.9029 | 0.7797 |
| **Decision Tree Classifier** | 0.7554 | 0.7531 | 0.7822 | 0.7745 | 0.7783 | 0.5056 |
| **K-Nearest Neighbor Classifier** | 0.8424 | 0.9293 | 0.8763 | 0.8333 | 0.8543 | 0.6839 |
| **Naive Bayes Classifier (Gaussian)** | 0.8750 | 0.9393 | 0.8559 | 0.9314 | 0.8920 | 0.7496 |
| **Ensemble Model (Random Forest)** | 0.8913 | 0.9393 | 0.8942 | 0.9118 | 0.9029 | 0.7797 |

---

## e. Detailed Performance Observations

1. **Logistic Regression & Ensemble Model (Random Forest)**:
   * **Observation**: Both models achieved the highest overall predictive accuracy of **89.13%** and an MCC score of **0.7797**. They demonstrate highly robust generalization on unseen clinical samples. Random Forest benefits from ensemble averaging, minimizing overfitting, while Logistic Regression functions exceptionally well with standard scaled numeric variables.
   
2. **Decision Tree Classifier**:
   * **Observation**: This model performed the poorest, yielding an accuracy of **75.54%** and an MCC of **0.5056**. Single decision trees are naturally prone to overfitting high-dimensional features and categorical splits, resulting in high variance and lower generalizability.

3. **K-Nearest Neighbor Classifier (KNN)**:
   * **Observation**: KNN achieved a moderate accuracy of **84.24%** and an F1 Score of **0.8543**. Since KNN depends entirely on distance boundaries, standardizing non-normally distributed continuous variables heavily affected its performance.

4. **Gaussian Naive Bayes Classifier**:
   * **Observation**: Naive Bayes reached a competitive **87.50%** accuracy and a remarkably high **Recall (Sensitivity) of 93.14%**. In medical screening, this model is highly valuable as it produces the fewest False Negatives, ensuring that patients carrying risks of cardiac issues are not missed.
