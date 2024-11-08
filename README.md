## Cholesterol Prediction using Ensemble and Stacking Models
- Table of Contents
- Introduction
- Project Overview
- Datasets Used
- Data Preprocessing
- Feature Engineering
- Modeling Approach
- Stacking and Meta-Model
- Evaluation Metrics
- Results
- Deployment
- Conclusion
- Future Work
- Acknowledgements
Introduction
This project aims to predict cholesterol levels using machine learning techniques on two separate health datasets. By leveraging feature engineering, advanced modeling techniques, and ensemble learning, this project attempts to create a robust predictive model that can assist in assessing cholesterol levels and identifying high-risk individuals.

Project Overview
Cholesterol levels are a significant indicator of cardiovascular health, with high cholesterol often linked to an increased risk of heart disease. This project uses two datasets—cholesterol.csv and framingham.csv—to build predictive models that estimate cholesterol levels based on various health metrics. The models are designed to be deployed for real-time predictions, providing an accessible tool for cholesterol risk assessment.

Datasets Used
Cholesterol Dataset (cholesterol.csv): Contains demographic and clinical data, including blood pressure, age, sex, and fasting blood sugar levels.
Framingham Dataset (framingham.csv): Derived from the Framingham Heart Study, this dataset includes variables such as cholesterol levels, smoking habits, BMI, blood pressure, and diabetes status.
Data Preprocessing
To ensure high-quality input data, we performed the following preprocessing steps:

Handling Missing Values: Missing values were imputed using a mix of median and mode for categorical data and the KNN Imputer for continuous variables, especially for glucose levels.
Outlier Handling: Outliers were identified using the IQR method, and certain variables like cigsPerDay were capped at predefined limits to minimize extreme values without losing critical information.
Standardization: Numerical features were standardized to ensure consistency across models and to improve model performance.
Feature Engineering
We created new features to capture complex relationships and interactions within the data:

Age Risk Index and Age Binning: Grouped age into categories to capture the non-linear relationship between age and cholesterol levels.
Cholesterol and Age Ratio: Calculated the cholesterol-to-age ratio as a relative measure of risk.
Metabolic Syndrome Indicator: Combined BMI, blood pressure, and diabetes status into a single feature to identify metabolic syndrome risks.
High Cholesterol Indicator: Flagged individuals with cholesterol levels above 200 mg/dL as high risk.
Interaction Terms: Created several interaction terms such as sysBP_BMI_interaction, cholesterol_gender_interaction, and currentSmoker_intensity to capture combined effects between features.
Modeling Approach
We trained separate models on each dataset (cholesterol.csv and framingham.csv) using the following approaches:

Random Forest Regressor
Gradient Boosting Regressor
Ridge Regression
Each model was tuned through GridSearchCV to identify the best hyperparameters. Performance was measured using metrics such as Mean Squared Error (MSE), R-squared, and Mean Absolute Error (MAE).

Stacking and Meta-Model
To combine the predictive power of both models, we implemented a stacking approach:

Truncated Predictions: Since the datasets were of different sizes, predictions from each model were truncated to the length of the shorter dataset.
Meta-Features Creation: Created a new dataset with predictions from each model as meta-features.
Meta-Model Training: A Gradient Boosting Regressor was used as the meta-model, trained on the meta-features created from the truncated predictions.
Hyperparameter Tuning: GridSearchCV was used to fine-tune the meta-model.
Evaluation Metrics
The model’s performance was evaluated using the following metrics:

Mean Squared Error (MSE): Measures the average squared difference between predicted and actual values.
R-squared (R²): Indicates the proportion of variance explained by the model.
Mean Absolute Error (MAE): Captures the average absolute difference between predicted and actual values.
Results
The stacked model significantly outperformed individual models, achieving:

Final Model Performance:
MSE:0.033833724166396024
R-squared:  0.9412343905092446
MAE: 0.15326840154382593
The model demonstrated strong predictive capability, especially in identifying high cholesterol levels.

Deployment
The final model was deployed using Flask, providing an interactive web interface that allows users to enter health metrics and receive real-time cholesterol risk assessments. SHAP values were also used to interpret predictions, offering transparency into the model's decision-making process.

Conclusion
This project successfully demonstrates how ensemble learning and stacking techniques can improve cholesterol prediction models. By combining features from multiple datasets and leveraging meta-modeling, the stacked model provides a reliable tool for cholesterol level assessment.

Future Work
Future improvements could include:

Integration with Additional Datasets: Incorporating more datasets to improve generalizability.
Model Explainability Enhancements: Leveraging additional interpretability methods like LIME alongside SHAP.
Mobile or Web App Development: Developing a user-friendly mobile or web app for broader accessibility

Acknowledgements
This project was completed as part of an internship at ICT Academy, Kerala. Special thanks to the mentors for their guidance on machine learning best practices.
