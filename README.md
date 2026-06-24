Power System Load Type Prediction
Overview
This project focuses on predicting the operational load category of a power system using historical energy consumption data. The objective is to classify power usage into one of the following categories:
·      Light_Load
·      Medium_Load
·      Maximum_Load
The solution follows a complete machine learning workflow, including data preprocessing, exploratory data analysis (EDA), feature engineering, model training, hyperparameter tuning, and model evaluation.

Problem Statement
Power systems experience varying load patterns throughout the day and across seasons. Accurately predicting the load category can help optimize energy distribution, improve resource planning, and support efficient power management.
Given historical measurements such as energy consumption, reactive power, power factor, CO₂ emissions, and time information, the goal is to build a classification model that predicts the corresponding load type.

Dataset Description
The dataset contains operational measurements collected from an industrial power system.
Features
Feature
Description
Date_Time
Timestamp of observation
Usage_kWh
Energy consumption (kWh)
Lagging_Current_Reactive.Power_kVarh
Lagging reactive power
Leading_Current_Reactive_Power_kVarh
Leading reactive power
CO2(tCO2)
CO₂ emissions
Lagging_Current_Power_Factor
Lagging power factor
Leading_Current_Power_Factor
Leading power factor
NSM
Number of Seconds from Midnight
Load_Type
Target variable
Target Classes
·      Light_Load
·      Medium_Load
·      Maximum_Load

Project Workflow
1. Data Preprocessing
The following preprocessing steps were performed:
·      Converted timestamp column to datetime format
·      Checked and handled missing values
·      Verified data quality and consistency
·      Encoded target labels for model training
·      Applied feature scaling where required

2. Exploratory Data Analysis (EDA)
EDA was conducted to understand data characteristics and identify patterns.
Analysis included:
·      Class distribution analysis
·      Feature correlation analysis
·      Statistical summaries
·      Temporal trend visualization
·      Distribution plots for numerical variables
Key observations helped guide feature engineering and model selection.

3. Feature Engineering
To improve model performance, several domain-inspired and temporal features were created.
Temporal Features
·      Hour of day
·      Month
·      Weekend indicator
Cyclical Encoding
Time-related variables are cyclical in nature. For example, 23:00 and 00:00 are only one hour apart but appear numerically distant.
To preserve this relationship:
·      hour_sin
·      hour_cos
·      month_sin
·      month_cos
were generated using sine and cosine transformations.
Power System Features
·      Total Reactive Power
·      Apparent Power
·      Power Factor Ratio
These engineered features provide additional information about the operational state of the power system.

Model Development
Multiple classification algorithms were evaluated and compared.
Models explored include:
·      Logistic Regression
·      Random Forest Classifier
·      XGBoost Classifier
Hyperparameter tuning was performed to identify the best-performing model.

Validation Strategy
To simulate real-world deployment and avoid data leakage, a time-based validation strategy was used.
·      Historical data used for training
·      Last month of available data reserved as test data
This approach evaluates the model’s ability to generalize to future unseen observations.

Evaluation Metrics
Model performance was assessed using:
·      Accuracy
·      Precision
·      Recall
·      F1-Score
·      Confusion Matrix
These metrics provide a comprehensive evaluation of classification performance across all load categories.

Results
The final selected model achieved strong classification performance on the hold-out test dataset and demonstrated its ability to distinguish between different power system load conditions.
Feature engineering and temporal encoding significantly contributed to improving predictive performance.

Technologies Used
Programming Language
·      Python
Libraries
·      Pandas
·      NumPy
·      Matplotlib
·      Seaborn
·      Scikit-Learn
·      XGBoost
·      Joblib
Development Environment
·      Jupyter Notebook

Project Structure
├── load_type_prediction.ipynb ├── load_data.csv ├── README.md └── model_artifacts/

How to Run
1. Clone Repository
git clone <repository-url> cd power-system-load-prediction
2. Install Dependencies
pip install -r requirements.txt
3. Launch Notebook
jupyter notebook
4. Run All Cells
Execute the notebook sequentially to:
·      Load and preprocess data
·      Perform EDA
·      Train models
·      Evaluate performance
·      Generate predictions

Future Improvements
·      Incorporate additional weather and environmental variables
·      Experiment with deep learning architectures
·      Deploy the model using FastAPI or Streamlit
·      Implement real-time load prediction capabilities

Author
Yamini Singh
M.Tech Computer Science Engineering
Machine Learning & Data Science Enthusiast
