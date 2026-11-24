# ⚡ SMARTWATT AI – Intelligent Energy Consumption Prediction & Anomaly Detection

### Machine Learning-Based Smart Energy Monitoring System

SMARTWATT AI is a machine learning-based project designed to analyze household electricity consumption, predict future energy usage, and detect unusual consumption patterns.

The system uses historical electricity consumption data to understand usage trends, forecast upcoming consumption, and identify potential energy anomalies using machine learning algorithms.

## 🎯 Project Objectives

- Analyze daily household electricity consumption.
- Predict future electricity consumption using historical data.
- Detect unusual electricity consumption patterns.
- Compare traditional and improved anomaly detection models.
- Support intelligent energy monitoring and management.

## 📊 Dataset

**Dataset:** Household Electric Power Consumption

**Source:** UCI Machine Learning Repository

The dataset contains household electricity consumption measurements recorded at one-minute intervals.

### Data Preprocessing

- Converted electricity consumption columns into numeric format.
- Combined Date and Time into a datetime column.
- Handled missing values.
- Aggregated minute-level readings into daily energy consumption.
- Converted daily electricity consumption into kWh.
- Retained days with at least 1,300 valid readings.

## 🧠 Machine Learning Components

### 1. Electricity Consumption Prediction – Random Forest Regression

Random Forest Regression is used to predict future household electricity consumption based on historical consumption patterns.

**Features used:**
- Previous day's consumption (`lag_1`)
- Consumption from two days earlier (`lag_2`)
- Consumption from seven days earlier (`lag_7`)
- Seven-day rolling average
- Seven-day rolling standard deviation
- Day of the week
- Month

**Model configuration:**
- Algorithm: Random Forest Regressor
- Number of estimators: 300
- Maximum depth: 8
- Minimum samples per leaf: 2
- Train-test split: 80:20 (time-ordered)

**Evaluation metrics:**
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

Additional regression models were compared:
- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- Gradient Boosting Regressor

### 2. Electricity Consumption Anomaly Detection – Isolation Forest

Isolation Forest is an unsupervised machine learning algorithm used to identify unusual electricity consumption patterns.

Two models were developed and compared.

**Original Isolation Forest**

- Uses only daily energy consumption (`energy_kwh`).
- Identifies unusual consumption values.

**Improved Isolation Forest**

Uses six historical and time-based features:

1. `energy_kwh`
2. `lag_1`
3. `lag_7`
4. `rolling_mean_7`
5. `rolling_std_7`
6. `day_of_week`

**Model configuration:**
- Algorithm: Isolation Forest
- Number of estimators: 200
- Contamination: 0.05
- Random state: 42
- Preprocessing: StandardScaler

The improved model considers historical consumption patterns and time-based information to identify unusual energy usage.

## 📈 Anomaly Detection Results

| Description | Result |
|---|---:|
| Total observations | 164 |
| Normal observations | 155 |
| Detected anomalies | 9 |
| Original model anomalies | 9 |
| Model agreements | 152 |
| Model disagreements | 12 |

**Selected Model:** Improved Isolation Forest

**Reason:** It considers historical consumption patterns and time-based features rather than relying only on individual energy consumption values.

*Note: Model agreement is not classification accuracy. The dataset does not contain verified ground-truth anomaly labels.*

## 🛠️ Technologies & Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Joblib
- Streamlit

```

## 🚀 Run the Application Locally

**Step 1:** Clone the repository.

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

**Step 2:** Navigate to the project directory.

```bash
cd SmartWatt-AI
```

**Step 3:** Install the required dependencies.

```bash
pip install -r requirements.txt
```

**Step 4:** Run the Streamlit application.

```bash
streamlit run app.py
```

## 🌐 Deployment

The project is prepared for deployment using Streamlit Community Cloud.

The deployment repository includes the Streamlit application, daily energy consumption data, trained anomaly detection model, scaler, and feature configuration.

## 🔮 Future Enhancements

- Real-time electricity consumption monitoring.
- Automated alerts for unusual energy usage.
- IoT-based smart meter integration.
- Interactive energy consumption dashboards.
- Advanced energy consumption forecasting.

---

**SMARTWATT AI – Making Energy Monitoring Smarter with Machine Learning.**
