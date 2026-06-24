# ⚡ Power System Load Type Prediction

## 📌 Project Overview

This project develops a Machine Learning classification model to predict the **Load Type** of a power system based on historical energy consumption and electrical measurements.

The target classes are:

* **Light_Load**
* **Medium_Load**
* **Maximum_Load**

The solution follows a complete Machine Learning pipeline including:

* Data Preprocessing
* Exploratory Data Analysis (EDA)
* Feature Engineering
* Model Training
* Hyperparameter Tuning
* Model Evaluation
* Prediction and Interpretation

---

# 🎯 Objective

The objective is to accurately classify the operating load condition of a power system using historical power consumption data and electrical characteristics.

Accurate load classification can help in:

* Energy management
* Load balancing
* Resource optimization
* Demand forecasting
* Power system monitoring

---

# 📂 Dataset Description

The dataset contains measurements collected from an industrial power system.

| Feature                              | Description                     |
| ------------------------------------ | ------------------------------- |
| Date_Time                            | Timestamp of observation        |
| Usage_kWh                            | Energy consumption in kWh       |
| Lagging_Current_Reactive.Power_kVarh | Lagging reactive power          |
| Leading_Current_Reactive_Power_kVarh | Leading reactive power          |
| CO2(tCO2)                            | Carbon dioxide emissions        |
| Lagging_Current_Power_Factor         | Lagging power factor            |
| Leading_Current_Power_Factor         | Leading power factor            |
| NSM                                  | Number of seconds from midnight |
| Load_Type                            | Target variable                 |

### Target Classes

* Light_Load
* Medium_Load
* Maximum_Load

---

# 🛠️ Technologies Used

### Programming Language

* Python 3.x

### Libraries

* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-Learn
* XGBoost
* Joblib

### Development Environment

* Jupyter Notebook

---

# 📊 Exploratory Data Analysis (EDA)

EDA was performed to understand the dataset and identify patterns affecting load type.

The following analyses were conducted:

* Dataset shape and structure
* Missing value analysis
* Target class distribution
* Feature distributions
* Correlation analysis
* Time-based consumption trends
* Statistical summaries

---

# ⚙️ Feature Engineering

Feature engineering was applied to improve model performance and capture temporal patterns.

## 1. Cyclical Time Encoding

Time-based variables are cyclical in nature.

For example:

* 23:00 and 00:00 are only one hour apart
* December and January are consecutive months

To preserve this relationship:

```python
hour_sin = sin(2π × hour / 24)
hour_cos = cos(2π × hour / 24)

month_sin = sin(2π × month / 12)
month_cos = cos(2π × month / 12)
```

These transformations allow the model to better learn periodic patterns.

---

## 2. Weekend Indicator

```python
is_weekend
```

Captures differences in power consumption between weekdays and weekends.

---

## 3. Power System Features

### Apparent Power

Represents overall electrical load behavior.

### Total Reactive Power

```python
Lagging Reactive Power + Leading Reactive Power
```

Provides information about the total reactive component of the system.

### Power Factor Ratio

Measures the relationship between lagging and leading power factors.

---

# 🤖 Machine Learning Models

Multiple classification models were trained and compared:

### Logistic Regression

* Fast baseline model
* Easy interpretability

### Random Forest Classifier

* Ensemble learning approach
* Handles nonlinear relationships effectively

### XGBoost Classifier

* Gradient boosting algorithm
* High predictive performance
* Robust to complex feature interactions

---

# ✅ Validation Strategy

To avoid data leakage and simulate real-world deployment:

* Historical data used for training
* Last month of observations used as the test set

This time-based split ensures the model is evaluated on future unseen data.

---

# 📈 Evaluation Metrics

The following classification metrics were used:

* Accuracy
* Precision
* Recall
* F1-Score
* Confusion Matrix

These metrics provide a comprehensive assessment of model performance across all load categories.

---

# 🏆 Results

The final model successfully classified power system load conditions with high accuracy.

Key achievements:

* Effective temporal feature engineering
* Strong classification performance
* Successful handling of cyclical time patterns
* Good generalization on unseen test data

---

# 📁 Project Structure

```text
Power-System-Load-Prediction/
│
├── load_type_prediction.ipynb
├── load_data.csv
├── README.md
│
└── model_artifacts/
```

---

# 🚀 How to Run

## 1. Clone Repository

```bash
git clone <repository-url>
cd Power-System-Load-Prediction
```

## 2. Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost joblib
```

## 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

## 4. Run Notebook

Execute all cells in:

```text
load_type_prediction.ipynb
```

The notebook will:

* Load data
* Perform preprocessing
* Generate engineered features
* Train models
* Evaluate performance
* Produce predictions

---

# 🔮 Future Improvements

Potential enhancements include:

* Incorporating weather information
* Real-time load prediction
* Model deployment using FastAPI or Streamlit
* Automated retraining pipeline
* Explainable AI using SHAP values

---

# 👩‍💻 Author

**Yamini Singh**

M.Tech – Computer Science Engineering

Machine Learning & Data Science Enthusiast

---

## Assignment Information

This project was completed as part of a Machine Learning assessment focused on solving a real-world classification problem using industry-standard ML practices including preprocessing, feature engineering, model selection, validation, and evaluation.
