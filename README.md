# 🏥 Insurance Cost Analysis & Feature Engineering

<div align="center">

### 📊 Exploratory Data Analysis • 🧹 Data Cleaning • ⚙️ Preprocessing • 🧠 Feature Engineering • 📐 Feature Selection

**A complete beginner-friendly data analysis and preprocessing project on medical insurance data using Python.**

<br>

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C8CBF?style=for-the-badge)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C?style=for-the-badge)
![Scikit--learn](https://img.shields.io/badge/Scikit--learn-Preprocessing-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)

</div>

---

## 📌 Table of Contents

- [📖 About the Project](#-about-the-project)
- [🎯 Project Objectives](#-project-objectives)
- [📂 Dataset](#-dataset)
- [🛠️ Technologies Used](#️-technologies-used)
- [🔄 Project Workflow](#-project-workflow)
- [🔍 Exploratory Data Analysis](#-exploratory-data-analysis)
- [🧹 Data Cleaning](#-data-cleaning)
- [⚙️ Data Preprocessing](#️-data-preprocessing)
- [🧩 Feature Engineering](#-feature-engineering)
- [📏 Feature Scaling](#-feature-scaling)
- [📊 Feature Analysis & Selection](#-feature-analysis--selection)
- [📋 Final Dataset](#-final-dataset)
- [📁 Project Structure](#-project-structure)
- [🚀 How to Run](#-how-to-run)
- [💡 Key Learnings](#-key-learnings)
- [🔮 Future Improvements](#-future-improvements)
- [👨‍💻 Author](#-author)

---

## 📖 About the Project

This project performs a complete **Exploratory Data Analysis (EDA) and data preprocessing workflow** on a medical insurance dataset.

The main purpose is to understand the dataset, clean the data, convert categorical values into machine-readable form, create useful derived features, scale numerical features, and analyze which features have a meaningful relationship with **insurance charges**.

> 🎯 **Target Variable:** `charges`

The project is implemented in a Jupyter Notebook using Python's data analysis and machine learning libraries.

---

## 🎯 Project Objectives

The project focuses on the following objectives:

- 🔎 Understand the structure of the insurance dataset
- 📊 Explore numerical and categorical variables
- 🧹 Detect and remove duplicate records
- 🔄 Convert categorical values into numerical values
- 🏷️ Rename columns for clearer interpretation
- 🧩 Encode categorical variables using one-hot encoding
- 🧠 Create BMI and age categories
- 📏 Apply feature scaling to numerical features
- 📈 Analyze correlation with insurance charges
- 🧪 Apply Chi-Square testing to categorical features
- 🎯 Prepare a cleaner and more relevant final dataset for further analysis or machine learning

---

## 📂 Dataset

The dataset contains **1,338 records** and **7 original features**.

### Original Features

| Feature | Description | Type |
|---|---|---|
| `age` | Age of the individual | Numerical |
| `sex` | Biological sex category | Categorical |
| `bmi` | Body Mass Index | Numerical |
| `children` | Number of children/dependents | Numerical |
| `smoker` | Smoking status | Categorical |
| `region` | Residential region | Categorical |
| `charges` | Medical insurance charges | Numerical / Target |

### Dataset Cleaning Result

- 📥 Original rows: **1,338**
- 🔍 Duplicate rows detected: **1**
- 🧹 Duplicate rows removed: **1**
- ✅ Rows after cleaning: **1,337**

---

## 🛠️ Technologies Used

### 🐍 Programming Language
- **Python**

### 📦 Libraries

```text
pandas
numpy
seaborn
matplotlib
scikit-learn
scipy
```

### 💻 Environment
- Jupyter Notebook
- VS Code / Jupyter-compatible environment

---

## 🔄 Project Workflow

```text
📥 Load Dataset
      │
      ▼
🔍 Initial Data Inspection
      │
      ▼
📊 Exploratory Data Analysis
      │
      ▼
🧹 Data Cleaning
      │
      ▼
⚙️ Categorical Encoding
      │
      ▼
🧩 Feature Engineering
      │
      ▼
📏 Feature Scaling
      │
      ▼
📈 Correlation Analysis
      │
      ▼
🧪 Chi-Square Feature Selection
      │
      ▼
🎯 Final Feature Dataset
```

---

## 🔍 Exploratory Data Analysis

The project starts by understanding the dataset before modifying it.

### Basic Inspection

The following operations are performed:

```python
df.shape
df.head()
df.info()
df.describe()
df.isnull().sum()
```

These help understand:

- Number of rows and columns
- First few records
- Data types
- Statistical summary
- Missing values

### 📊 Visualizations

The project uses visualizations to understand the distribution of:

- 👤 Age
- ⚖️ BMI
- 👶 Number of children
- 💰 Insurance charges
- 🚻 Sex
- 🚬 Smoking status

It also uses box plots to inspect numerical distributions and a correlation heatmap to understand relationships between numerical variables.

---

## 🧹 Data Cleaning

A copy of the original dataset is created before cleaning:

```python
df_cleaned = df.copy()
```

### Duplicate Detection

```python
df_cleaned.duplicated().sum()
```

The analysis identified **1 duplicate row**.

It was removed using:

```python
df_cleaned.drop_duplicates(inplace=True)
```

After cleaning, the dataset contains **1,337 rows**.

---

## ⚙️ Data Preprocessing

### 1️⃣ Encoding `sex`

The categorical values are converted into numerical values:

```text
male   → 0
female → 1
```

The column is then renamed:

```text
sex → is_female
```

This makes the meaning of the encoded value clearer.

---

### 2️⃣ Encoding `smoker`

The smoking status is converted:

```text
yes → 1
no  → 0
```

The column is renamed:

```text
smoker → is_smoker
```

---

### 3️⃣ One-Hot Encoding `region`

The `region` column contains four categories:

```text
northeast
northwest
southeast
southwest
```

One-hot encoding creates separate binary columns:

```text
region_northeast
region_northwest
region_southeast
region_southwest
```

---

## 🧩 Feature Engineering

Feature engineering creates additional information from existing variables.

### ⚖️ BMI Categories

The project converts BMI into four categories:

| BMI Range | Category |
|---|---|
| ≤ 18.9 | Underweight |
| 19.0 – 24.9 | Normal |
| 25.0 – 29.9 | Overweight |
| ≥ 30 | Obese |

These categories are then one-hot encoded.

---

### 👤 Age Categories

Age is also converted into categories:

| Age Range | Category |
|---|---|
| ≤ 18 | UnderAged |
| 19 – 60 | Young |
| 61 – 80 | Adult |
| > 80 | Old |

These categories are then one-hot encoded.

> ℹ️ These age labels are the categories defined in the notebook and are kept here exactly for consistency with the project.

---

## 📏 Feature Scaling

The project applies `StandardScaler` to:

```python
['age', 'bmi', 'children']
```

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

df_cleaned[cols] = scaler.fit_transform(df_cleaned[cols])
```

### 🤔 Why scaling?

Feature scaling puts numerical features onto a comparable scale.

For example:

```text
Age       → values around 18–64
BMI       → values around 15–53
Children  → values around 0–5
```

After standardization, these variables are represented on a common standardized scale.

---

## 📊 Feature Analysis & Selection

### 🔗 Correlation Analysis

The project calculates the correlation of numerical features with `charges`.

The strongest positive correlation observed in the processed dataset is:

```text
is_smoker → ~0.787
```

Other notable positive correlations include:

```text
age → ~0.298
bmi → ~0.198
children → ~0.067
```

Correlation is used here as an exploratory measure of linear association; it does **not** by itself prove causation.

---

### 🧪 Chi-Square Feature Selection

For categorical/binary features, the project uses the **Chi-Square test of independence**.

The significance level is:

```python
alpha = 0.05
```

Insurance charges are divided into four quantile-based groups using:

```python
pd.qcut(df_cleaned['charges'], q=4)
```

The Chi-Square test is then applied between each categorical feature and the charge groups.

### 📌 Features marked to keep by the notebook's test

Using the notebook's rule:

```text
p-value < 0.05 → Reject Null → Keep Feature
```

the following features were marked as **Keep**:

- `is_smoker`
- `age_category_Adult`
- `age_category_UnderAged`
- `age_category_Young`
- `region_southeast`
- `is_female`

Features with `p-value >= 0.05` were marked for removal by this specific test.

> ⚠️ Statistical feature selection depends on the chosen test, assumptions, target representation, and significance threshold. A feature not selected by one test is not automatically useless for every machine-learning model.

---

## 📋 Final Dataset

The notebook creates a final dataframe containing these columns:

```text
age
is_female
bmi
children
is_smoker
charges
region_southeast
age_category_Adult
age_category_UnderAged
age_category_Young
```

### 🎯 Final Structure

```text
Numerical Features
├── age
├── bmi
└── children

Encoded Features
├── is_female
├── is_smoker
└── region_southeast

Engineered Features
├── age_category_Adult
├── age_category_UnderAged
└── age_category_Young

Target
└── charges
```

---

## 📁 Project Structure

```text
Insurance-Analysis/
│
├── 📓 Insurance.ipynb
├── 📊 insurance.csv
└── 📄 README.md
```

> If your dataset filename is different in your repository, update the filename in the notebook and this section accordingly.

---

## 🚀 How to Run

### 1️⃣ Clone the repository

```bash
git clone <your-repository-url>
```

### 2️⃣ Open the project

```bash
cd Insurance-Analysis
```

### 3️⃣ Install required libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter
```

### 4️⃣ Start Jupyter Notebook

```bash
jupyter notebook
```

### 5️⃣ Open

```text
Insurance.ipynb
```

### 6️⃣ Run the cells

Run the notebook from top to bottom to reproduce the analysis.

---

## 💡 Key Learnings

Through this project, the following concepts are practiced:

- 🐼 Pandas DataFrame operations
- 🔢 NumPy basics
- 🔍 Exploratory Data Analysis
- 📊 Data visualization
- 🧹 Duplicate data cleaning
- 🔤 Categorical encoding
- 🏷️ Column renaming
- 🧩 Feature engineering
- 📏 Standardization
- 🔗 Correlation analysis
- 🧪 Chi-Square statistical testing
- 🎯 Feature selection
- 📓 Jupyter Notebook workflow

---

## 🔮 Future Improvements

This project currently focuses on **EDA, preprocessing, feature engineering, and feature selection**.

Possible next steps:

- 🤖 Train regression models to predict `charges`
- 📈 Compare Linear Regression, Random Forest, Gradient Boosting, etc.
- 📊 Evaluate models using MAE, MSE, RMSE, and R²
- 🔄 Build a complete preprocessing pipeline
- 🎯 Perform systematic model-based feature selection
- 💾 Save the trained model using `joblib`
- 🌐 Build a simple prediction web application
- 📦 Deploy the application

---

## ⚠️ Project Scope

This repository represents a **data analysis and preprocessing workflow**.

It does **not currently contain a trained machine-learning prediction model or model performance evaluation** in the provided notebook.

That distinction is important: preprocessing prepares data for machine learning, but it is not the same thing as training and evaluating a predictive model.

---

## 👨‍💻 Author

**Devan Patel**

🎓 BSc Information Technology Student  
💻 Interested in Data Analytics, Machine Learning 

---

<div align="center">

### ⭐ If you found this project useful, consider giving the repository a star!

**Built with Python 🐍 | Data with Purpose 📊 | Learning with Every Project 🚀**

</div>
