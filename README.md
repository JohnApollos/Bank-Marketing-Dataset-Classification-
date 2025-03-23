# Client Term Deposit Subscription Analysis

## **Project Overview**
This repository contains the analysis of client subscription behavior for term deposits. Using a dataset with demographic, financial, and campaign-related features, we aim to uncover insights that can optimize marketing strategies and enhance client engagement. This documentation includes **Milestone 1** (EDA and preprocessing) and **Milestone 2** (feature transformation and model training).

---

## **Milestones**

### **Milestone 1: Exploratory Data Analysis and Preprocessing**

#### **1. Data Understanding**
The dataset contains information about clients, including their demographics, past interactions, financial status, and marketing outcomes. The target variable (`y`) indicates whether a client subscribed to a term deposit.

| Feature Name       | Description                                                                                   | Type            |
|--------------------|-----------------------------------------------------------------------------------------------|-----------------|
| `age`              | Age of the client                                                                            | Integer         |
| `job`              | Type of job (e.g., admin., blue-collar)                                                       | Categorical     |
| `marital`          | Marital status of the client (e.g., single, married)                                          | Categorical     |
| `education`        | Level of education (e.g., university.degree, basic.6y)                                        | Categorical     |
| `default`          | Has credit in default?                                                                       | Binary          |
| `balance`          | Average yearly balance in euros                                                              | Integer         |
| `housing`          | Has housing loan?                                                                            | Binary          |
| `loan`             | Has personal loan?                                                                           | Binary          |
| `contact`          | Contact communication type (e.g., cellular, telephone)                                       | Categorical     |
| `day_of_week`      | Last contact day of the week                                                                 | Date            |
| `month`            | Last contact month of year                                                                   | Date            |
| `duration`         | Duration of last contact (in seconds) - benchmark only; excluded from predictive modeling     | Integer         |
| `campaign`         | Number of contacts during the current campaign                                               | Integer         |
| `pdays`            | Days since last contact in previous campaign (-1 if not contacted before)                    | Integer         |
| `previous`         | Number of contacts performed before this campaign                                            | Integer         |
| `poutcome`         | Outcome of the previous campaign (e.g., success, failure)                                    | Categorical     |
| `y`                | Target variable - client subscribed a term deposit                                           | Binary          |

---

#### **2. Data Preprocessing**
1. **Handling Missing Values**:
   - `contact` and `poutcome`: Missing values replaced with `"unknown"`.
   - `pdays`: Missing values imputed with `-1` to signify no previous contact.

2. **Encoding Categorical Variables**:
   - **One-hot encoding** applied to `job`, `education`, `contact`, and `poutcome`.
   - **Binary encoding** used for `housing` and `loan`.

3. **Scaling Numerical Features**:
   - Standardized features such as `age`, `balance`, `campaign`, and `pdays`.

---

#### **3. Exploratory Data Analysis (EDA)**
1. **Key Insights**:
   - Higher subscription rates observed in students, retirees, and university-educated individuals.
   - Cellular contact methods are most effective.
   - Previous campaign success strongly predicts future subscription likelihood.

2. **Correlation Analysis**:
   - Revealed strong correlations between certain features (`previous`, `poutcome_success`).

---

### **Milestone 2: Feature Transformation and Model Training**

#### **1. Feature Transformation**
1. **Scaling**: Standardized numerical features using `StandardScaler`.
2. **Encoding**: Applied one-hot encoding to categorical features.

#### **2. Data Splitting**
- Divided the dataset into training (80%) and testing (20%) sets.

#### **3. Model Training**
Three machine learning models were trained:
1. **Logistic Regression**:
   - Baseline model to provide interpretable results.
2. **Random Forest**:
   - Ensemble model for robust performance and reduced overfitting.
3. **Gradient Boosting (XGBoost)**:
   - High-accuracy model suitable for structured datasets.

#### **4. Hyperparameter Tuning (Optional)**
- Performed grid search to optimize model parameters:
   - Random Forest: Tuned `n_estimators`, `max_depth`, `min_samples_split`.
   - XGBoost: Tuned `n_estimators`, `learning_rate`, `max_depth`.

---

## **Results and Outputs**
1. **Preprocessed Dataset**: Complete feature set ready for modeling.
2. **Trained Models**: Logistic Regression, Random Forest, and XGBoost.
3. **Best Hyperparameters** (optional):
   - **Random Forest**: Optimal number of trees and depth.
   - **XGBoost**: Ideal learning rate, depth, and number of estimators.

---

## **Next Steps**
The next milestone focuses on **model evaluation**, where we will assess the models’ performance using metrics such as accuracy, precision, recall, and F1-score. The best model will then be used for predictions.

---

## **Files and Directories**
- **`data/`**: Contains the dataset files (`df_X.csv`, `df_y.csv`, `info.csv`).
- **`notebooks/`**: Includes separate notebooks for each milestone:
   - `Bank Marketing Dataset_Milestone_1.ipynb`: Exploratory Data Analysis and Preprocessing.
   - `Bank Marketing Dataset_Milestone_2.ipynb`: Feature Transformation and Model Training.
- **`models/`**: Stores trained model artifacts (optional).
- **`README.md`**: Comprehensive project documentation.

---

## **Acknowledgments**
Thank you for visiting this repository! Feel free to contribute or raise issues if you have suggestions or questions.

---

## **License**
This project is licensed under [MIT License](LICENSE).
