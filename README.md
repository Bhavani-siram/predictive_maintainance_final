# Predictive Maintenance Using IoT Sensor Data

A machine learning project that uses IoT sensor telemetry to predict whether a catastrophic equipment failure is likely to occur within the next 24 hours.

## 📌 Project Overview

Predictive maintenance uses sensor data and machine learning to identify potential equipment failures before they occur. This project analyzes time-series IoT sensor telemetry and develops a machine learning model to predict upcoming failures.

The goal is to use historical sensor measurements such as temperature, vibration, and voltage to provide an early warning of potential equipment failure.

## 🎯 Objectives

- Analyze IoT sensor telemetry data.
- Identify patterns associated with equipment failures.
- Create meaningful time-based features from sensor measurements.
- Predict whether a catastrophic failure will occur within the next 24 hours.
- Evaluate the predictive performance using classification metrics and a confusion matrix.

## 📊 Dataset

The project uses the `iot_sensor_telemetry.csv` dataset.

The dataset contains 10,000 hourly sensor records with the following main attributes:

| Feature | Description |
|---|---|
| `Timestamp` | Date and time of the sensor reading |
| `Sensor_Temp_C` | Sensor temperature in Celsius |
| `Sensor_Vibration_mm` | Sensor vibration measurement |
| `Sensor_Voltage_V` | Sensor voltage measurement |
| `Catastrophic_Failure` | Historical equipment failure indicator |

## ⚙️ Feature Engineering

To capture temporal patterns in the sensor data, the following features were created:

- **12-hour rolling temperature mean** – represents the recent average temperature.
- **12-hour rolling vibration standard deviation** – captures recent variation in vibration.
- **Failure within 24 hours** – created by shifting the failure information 24 hours into the future.

The original failure column is removed after creating the future failure target to prevent target leakage.

## 🤖 Machine Learning Approach

The project follows a time-aware machine learning workflow:

1. Load and inspect the IoT sensor telemetry dataset.
2. Sort the observations chronologically.
3. Perform time-based feature engineering.
4. Create the 24-hour future failure target.
5. Handle missing values created by rolling and future-target calculations.
6. Remove the original failure indicator from the predictive features.
7. Split the data chronologically into training and testing sets.
8. Train a balanced **Random Forest Classifier**.
9. Evaluate the predictions using classification metrics and a confusion matrix.
10. Perform threshold-based evaluation to analyze the classification behavior.

## 🧠 Model

### Random Forest Classifier

A Random Forest classifier is used to learn relationships between sensor measurements and future equipment failures.

The model uses multiple decision trees and combines their predictions to produce the final classification.

Class balancing is used because catastrophic failures are much less frequent than normal operating conditions.

## 📈 Results

The project includes model evaluation using a confusion matrix and threshold-based analysis.

### Threshold-Based Confusion Matrix

The threshold-based evaluation produced the following confusion matrix:

**[[1973, 17], [1, 2]]**

## 🚀 Open in Google Colab

[Open the project in Google Colab](https://colab.research.google.com/drive/1IRo3BGZDp0o4RJEMC4AjCJRPipf16WZa?usp=sharing)
