# 🌫️ Air Quality Prediction

## 📌 Overview
This project focuses on predicting air quality using the Air Quality UCI dataset. The primary goal is to build and evaluate deep learning models that can forecast air quality levels based on various environmental factors. The notebook explores both classification and regression approaches to predict Carbon Monoxide (CO) levels.

---

## 📊 Dataset
The dataset used in this project is the **"Air Quality UCI Data Set,"** which contains over 8,000 instances of hourly averaged responses from an array of 5 metal oxide chemical sensors embedded in an Air Quality Chemical Multisensor Device.

### Features include:
- **Date and Time**: Timestamp of the recording.
- **CO(GT)**: True hourly averaged concentration of CO in mg/m³ (target variable for classification).
- **PT08.S1(CO)**: PT08.S1 (tin oxide) hourly averaged sensor response (nominally CO targeted).
- **NMHC(GT)**: True hourly averaged overall Non-Methane Hydrocarbons concentration in µg/m³.
- **C6H6(GT)**: True hourly averaged Benzene concentration in µg/m³.
- **PT08.S2(NMHC)**: PT08.S2 (titania) hourly averaged sensor response (nominally NMHC targeted).
- **NOx(GT)**: True hourly averaged NOx concentration in ppb (target variable for regression).
- **PT08.S3(NOx)**: PT08.S3 (tungsten oxide) hourly averaged sensor response (nominally NOx targeted).
- **NO2(GT)**: True hourly averaged NO2 concentration in µg/m³.
- **PT08.S4(NO2)**: PT08.S4 (tungsten oxide) hourly averaged sensor response (nominally NO2 targeted).
- **PT08.S5(O3)**: PT08.S5 (indium oxide) hourly averaged sensor response (nominally O3 targeted).
- **T**: Temperature in °C.
- **RH**: Relative Humidity (%).
- **AH**: Absolute Humidity.

---

## 🛠 Methodology
The project follows these key steps:

1. **Data Loading and Initial Exploration**  
   The dataset is loaded from an Excel file, and an initial analysis is performed to understand its structure and features.

2. **Data Preprocessing**
   - Missing values, represented as -200, are replaced with NaN.
   - Feature engineering is performed to extract year, month, day, and hour from the date and time columns.
   - Rows with missing target values (`CO(GT)` for classification and `NOx(GT)` for regression) are dropped.
   - Numerical features are imputed using a K-Nearest Neighbors (KNN) imputer and then scaled using a StandardScaler.

3. **Model Development**
   - **Classification**: A neural network is built to classify whether the `CO(GT)` level is above or below a certain threshold (the mean).
   - **Regression**: A separate neural network is developed to predict the continuous value of `NOx(GT)`.

4. **Model Training and Evaluation**  
   The models are trained on the preprocessed data, and their performance is evaluated using appropriate metrics. Early stopping is used to prevent overfitting.

---

## 🤖 Models

### 🔷 Classification Model
A sequential neural network with the following architecture is used:

- Input Layer  
- Dense Layer (64 units, ReLU activation)  
- Dense Layer (32 units, ReLU activation)  
- Dense Layer (16 units, ReLU activation)  
- Output Layer (1 unit, Sigmoid activation)  

**Optimizer**: Adam  
**Loss**: Binary Cross-Entropy  

---

### 🔶 Regression Model
A sequential neural network with dropout and L2 regularization:

- Input Layer  
- Dense Layer (128 units, ReLU activation, L2 regularization)  
- Dropout (0.5)  
- Dense Layer (64 units, ReLU activation, L2 regularization)  
- Dropout (0.3)  
- Dense Layer (32 units, ReLU activation, L2 regularization)  
- Dense Layer (16 units, ReLU activation, L2 regularization)  
- Output Layer (1 unit)  

**Optimizer**: Adam  
**Loss**: Mean Squared Error (MSE)  

---

## 📈 Results

### ✅ Classification Results
- **Test Accuracy**: 92.62%  
- **Precision**: 88.64%  
- **Recall**: 93.54%  
- **F1 Score**: 91.02%  

### 📉 Regression Results
- **Test RMSE**: 58.57  
- **Test MAE**: 38.53  

---

## 📌 Conclusion
The results indicate that the models perform well on both the classification and regression tasks, demonstrating their ability to predict air quality with a high degree of accuracy.

---
