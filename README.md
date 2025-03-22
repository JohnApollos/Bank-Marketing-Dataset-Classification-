# Client Term Deposit Subscription Analysis

## **Project Overview**
This repository contains the analysis of client subscription behavior for term deposits. Using a dataset with demographic, financial, and campaign-related features, we aim to uncover insights that can optimize marketing strategies and enhance client engagement. This documentation includes **Milestone 1**, which covers extensive Exploratory Data Analysis (EDA) and preprocessing of the data.

---

## **Milestone 1: Exploratory Data Analysis and Preprocessing**

### **1. Data Understanding**
#### **Dataset Overview**
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

### **2. Data Preprocessing**
#### **Handling Missing Values**
- **`contact` and `poutcome`:** Missing values were replaced with `"unknown"`.
- **`pdays`:** Missing values were imputed with `-1` to signify no previous contact.

#### **Encoding Categorical Variables**
- **One-hot encoding:** Applied to categorical variables such as `job`, `education`, `contact`, and `poutcome`, converting each category into a binary column.
- **Binary encoding:** Used for `housing` and `loan` features.

#### **Scaling Numerical Features**
- Numerical features like `age`, `balance`, `campaign`, and `pdays` were standardized for consistent scaling, ensuring compatibility with machine learning models.

---

### **3. Exploratory Data Analysis (EDA)**

#### **Summary Statistics**
Key metrics for numerical features were analyzed:
- Mean `age`: ~40 years
- Median yearly balance: ~€400
- High variability observed in `campaign` and `duration`.

#### **Visualizations and Key Insights**
1. **Job**:
   - **Subscription rates:**
     - Higher: `Student` (28%), `Retired` (25%)
     - Lower: `Blue-collar` (7%), `Unemployed` (8%)
   - **Insight:** Students and retired clients are highly likely to subscribe, while blue-collar workers and unemployed individuals require targeted strategies.

2. **Marital Status**:
   - **Subscription rates:**
     - Single: 14.4%
     - Divorced: 11.4%
     - Married: 9.6%
   - **Insight:** Singles show the highest likelihood of subscribing, whereas married clients have the lowest.

3. **Education Level**:
   - **Subscription rates:**
     - Higher: University degree (20%), Professional courses (17%)
     - Lower: Basic education levels (e.g., basic.4y: 4.5%)
   - **Insight:** Higher education levels correlate with higher subscription rates.

4. **Contact Type**:
   - **Subscription rates:**
     - Cellular: 13.7%
     - Telephone: 4.5%
     - Unknown: 2.5%
   - **Insight:** Cellular is the most effective contact method.

5. **Poutcome**:
   - **Subscription rates:**
     - Success: 65.3%
     - Failure: 13.8%
     - Nonexistent: 9.5%
   - **Insight:** Successful outcomes from previous campaigns strongly indicate future subscription likelihood.

#### **Correlation Analysis**
A correlation heatmap revealed:
- Strong positive correlation between `previous` and `poutcome_success`.
- Weak correlation between demographic features like `age` and the target variable (`y`).

---

### **4. Feature Importance**
Based on EDA, the following features are identified as significant for predictive modeling:
- **Highly Relevant:**
  - `job`
  - `education`
  - `contact`
  - `poutcome`
  - `balance`
- **Excluded:**
  - `duration` (not used for realistic predictions, per guidelines)

---

### **5. Recommendations**
1. **Marketing Strategies:**
   - Focus campaigns on high-performing groups like students, retirees, and university-educated individuals.
   - Leverage cellular contact methods for engagement.

2. **Next Steps:**
   - Perform cross-variable analysis (e.g., job and education level).
   - Build predictive models using identified features.

---

## **Future Milestones**
### **Milestone 2: Modeling**
Develop machine learning models for predicting term deposit subscription (`y`), leveraging insights from Milestone 1.

---

## **Acknowledgments**
Thank you for visiting this repository. If you have questions or suggestions, feel free to contribute or raise an issue.

---

## **License**
This project is licensed under [MIT License](LICENSE).
