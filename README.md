Predicting College Applications Using Machine Learning
Overview
This project focuses on predicting the number of college applications (Apps) received by U.S. colleges using various institutional and academic features. The goal is to help universities anticipate application volumes to optimize planning and resource allocation. The project was developed as part of the Data Science Fundamentals course at Tose’eh Institute.

Dataset Description
The dataset includes information from U.S. colleges in 1995 and contains the following variables:

Apps: Number of applications received (target variable).

Accept: Number of applicants accepted.

Enroll: Number of new students enrolled.

Top10perc: % of new students from the top 10% of their high school class.

Top25perc: % of new students from the top 25% of their high school class.

F.Undergrad: Number of full-time undergraduates.

P.Undergrad: Number of part-time undergraduates.

Outstate: Out-of-state tuition.

Room.Board: Room and board cost.

Books: Estimated book cost.

Personal: Estimated personal spending.

PhD: % of faculty with PhDs.

Terminal: % of faculty with terminal degrees.

S.F.Ratio: Student/faculty ratio.

perc.alumni: % of alumni who donate.

Expend: Instructional expenditure per student.

Grad.Rate: Graduation rate.

Methodology
Data Preprocessing:

Handled missing values and outliers.

Converted categorical variables.

Normalized numerical features where appropriate.

Exploratory Data Analysis (EDA):

Visualized distributions and outliers using boxplots and histograms.

Analyzed correlations using a heatmap.

Investigated relationships between Apps and predictor variables.

Modeling and Prediction:

Tested multiple regression models to predict the Apps variable:

Linear Regression

Decision Tree Regressor

Random Forest Regressor

Gradient Boosting Regressor

Performed hyperparameter tuning and cross-validation.

Evaluated model performance using:

RMSE (Root Mean Squared Error)

MAE (Mean Absolute Error)

R² Score

Key Findings
Strong Predictors: Features such as Outstate, PhD, F.Undergrad, and perc.alumni showed high correlation with Apps.

Non-Linear Models Performed Better: Tree-based models, especially Random Forest, yielded better predictive performance than linear models.

Data Quality Matters: Addressing outliers and normalizing skewed variables improved model accuracy significantly.

Regression Models
Linear Regression:

Simple and interpretable.

Moderate accuracy with some underfitting.

Random Forest Regressor:

Best performing model with the lowest RMSE and highest R².

Captured non-linear relationships effectively.

Gradient Boosting Regressor:

Performed well, but slightly overfit the training data.

Conclusion
Predicting college application volumes is feasible using machine learning and institutional features. Universities can leverage such models to enhance strategic planning in admissions and marketing. Ensemble models like Random Forest provide robust predictions due to their ability to model complex relationships in the data.

Repository Structure
notebook.ipynb: Jupyter Notebook containing the complete analysis and models.

college.csv: Dataset used in the analysis.

README.md: Overview and documentation of the project (this file).

How to Use
Clone the repository:

bash
Copy
Edit
git clone https://github.com/your-username/college-applications-prediction.git
Open notebook.ipynb in Jupyter Notebook or VS Code.

Run the cells to explore data analysis and model predictions.

Dependencies
Python 3.x

Libraries:

pandas

numpy

scikit-learn

matplotlib

seaborn

Author
Farid Mohammadzadeh

Supervisor: Dr. Farzad Minooei

For any questions or feedback, feel free to contact Farid Mohammadzadeh.
