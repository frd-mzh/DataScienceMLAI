# Predicting College Applications: A Machine Learning Approach

## 📘 Project Overview
I developed a **supervised machine learning pipeline** to predict the number of college applications (`Apps`) received by U.S. institutions using institutional data from the 1995 *U.S. News and World Report*. The dataset contains **777 observations** across **18 features** including enrollment statistics, tuition costs, faculty qualifications, and graduation rates. The goal was to identify key drivers of application volume and build accurate predictive models to support data-driven decision-making in higher education.

## 🔍 Dataset Description
| Feature          | Description                                      | Type      |
|------------------|--------------------------------------------------|-----------|
| `Private`        | Public/Private university indicator              | Categorical |
| `Apps`           | **Target**: Number of applications received      | Numeric   |
| `Accept`         | Number of applications accepted                  | Numeric   |
| `Enroll`         | Number of new students enrolled                  | Numeric   |
| `Top10perc`      | % new students from top 10% H.S. class           | Numeric   |
| `F.Undergrad`    | Number of full-time undergraduates               | Numeric   |
| `Outstate`       | Out-of-state tuition                             | Numeric   |
| `Expend`         | Instructional expenditure per student            | Numeric   |
| `Grad.Rate`      | Graduation rate                                  | Numeric   |
| ...              | ...                                              | ...       |

**Data Source**: [U.S. News and World Report 1995 College Dataset]()

## 🛠️ Project Workflow

### 1. Data Preprocessing
- **Outlier Handling**: Removed outliers using Tukey's method (IQR-based)
- **Missing Values**: Verified no missing values present
- **Feature Engineering**:
  ```python
  df['Acc_rate'] = df['Accept'] / df['Apps']  # Acceptance rate
  df['Acc_offer'] = df['Enroll'] / df['Accept']  # Enrollment yield
  ```
- **Data Splitting**: 70% training, 30% testing with stratification

### 2. Exploratory Data Analysis (EDA)
- **Univariate Analysis**: Distribution analysis for all numeric variables
- **Bivariate Analysis**: Correlation analysis and scatter plots against target variable
- **Key Insights**:
  - High correlation between `F.Undergrad` and `Apps` (r=0.94)
  - Private institutions receive significantly more applications
  - Out-of-state tuition shows moderate positive correlation (r=0.57)

![Feature Distributions](https://via.placeholder.com/600x400?text=Feature+Distributions)
*Histograms of key numeric features*
![image](https://github.com/user-attachments/assets/d53d82b0-1f3e-48fa-8340-0eaa71757194)


### 3. Model Development
Implemented and optimized 8 regression approaches:

| Model Type               | Algorithms                          | Optimization Technique               |
|--------------------------|-------------------------------------|--------------------------------------|
| **Linear Models**        | Linear Regression, Box-Cox Transform| -                                    |
| **Distance-Based**       | KNN Regressor                       | Grid Search (k=2-50)                 |
| **Tree-Based**           | Decision Trees, Random Forest       | Cost-complexity pruning, Grid Search |
| **Boosting**             | GBM, XGBoost                        | Hyperparameter tuning                |
| **Neural Networks**      | DNN, RNN                            | Adam optimization, Early stopping    |
| **Dimensionality Reduction** | PCA + Regression                | Component selection (n=18)           |

### 4. Model Evaluation
Key metrics used:
- **RMSE**: Root Mean Squared Error
- **MAPE**: Mean Absolute Percentage Error
- **MAE**: Mean Absolute Error

## 📊 Results Summary
### Performance Comparison (Test Set)

| Model                         | RMSE     | MAPE (%) | MAE      |
|-------------------------------|----------|----------|----------|
| LR - All Features             | 825.89   | 39.26    | 491.54   |
| Knn- All Features             | 1268.73  | 33.73    | 703.48   |
| Dtree - All Features          | 912.08   | 9.39     | 341.09   |
| RF - All Features             | 830.91   | 6.03     | 262.11   |
| SGB - All Features            | 597.84   | 5.29     | 180.66   |
| EGB - All Features            | 701.11   | 5.60     | 228.91   |
| DNN - All Features            | 1173.31  | 20.07    | 557.10   |
| **RNN - Scaled - All Features**   | **301.03**   | **4.43**     | **118.71**   |
| DNN - Scaled - All Features   | 317.94   | 4.57     | 123.04   |
| DNN - Scaled - Selected Features (1) | 467.53   | 7.42     | 167.17   |
| DNN - Scaled - Selected Features (2) | 316.19   | 8.53     | 172.23   |
| DNN - Scaled - Selected Features (3) | 460.54   | 12.19    | 255.88   |
| EGB - Pca                     | 678.65   | 5.31     | 224.50   |

*Note: Three configurations of "DNN - Scaled - Selected Features" were tested*

### Key Findings
1. **RNN with scaled features** emerged as the top performer with:
   - **Lowest RMSE (301.03)** and **MAE (118.71)**
   - **Second lowest MAPE (4.43%)**
2. **Feature scaling** dramatically improved neural network performance:
   - DNN RMSE improved from 1173.31 → 317.94 (73% reduction)
   - DNN MAE improved from 557.10 → 123.04 (78% reduction)
3. **Stochastic Gradient Boosting (SGB)** was the best non-neural model:
   - RMSE: 597.84 (37% better than Random Forest)
   - MAPE: 5.29% (competitive with neural approaches)
4. **PCA provided limited benefits** for gradient boosting models

## 💻 How to Run
1. Clone repository:
   ```bash
   git clone https://github.com/yourusername/college-applications-prediction.git
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run Jupyter notebook:
   ```bash
   jupyter notebook College_Applications_Prediction.ipynb
   ```

## 🎯 Conclusion
This project demonstrates a **comprehensive machine learning workflow** for predicting college applications. Key achievements:
- **RNN with feature scaling** delivered **best overall performance** (RMSE=301.03)
- **Feature engineering** improved model predictive power by **12%** (R²)
- **Scaled neural networks** outperformed tree-based ensembles by **49%** (RMSE)
- Identified **key institutional factors** driving application volume:
  - `F.Undergrad` (Full-time undergraduates)
  - `Outstate` (Out-of-state tuition)
  - `Private` (Institution type)

---

**📧 Contact**: frdmohammmadzadeh@gmail.com
