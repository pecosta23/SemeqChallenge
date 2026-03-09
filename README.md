# Main Objective

This project aims to identify types of mechanical failures based on patterns reported by sensors from the **Machinery Fault Dataset (MAFAULDA)**.

# Dataset

The dataset contains sensor data collected from a **Mechanical Failure Simulator (MFS)**.

Two classes were considered:

- **Normal**
- **Imbalance** (different levels of imbalance)

# Preprocessing

### 1. StandardScaler and Statistical Features

The following statistical features were extracted:

- RMS (Root Mean Square)
- Mean
- Standard Deviation
- Skewness
- Kurtosis

After feature extraction, the data was standardized using **StandardScaler**.

These features summarize the global behavior of the data and are widely used in **predictive maintenance** due to their interpretability and reliability.

### 2. Fast Fourier Transform (FFT)

The **Fast Fourier Transform** was applied to extract the first components of the frequency spectrum.

Mechanical failures often produce specific discrepancies in vibration signals, making **FFT a viable technique for fault diagnosis**.

# Models

## Random Forest Classifier

- Robust against noisy data
- Good performance without significant overfitting
- Relatively interpretable
- Good generalization capability

## XGBoost Classifier

- Used with FFT-based features
- High capacity for nonlinear modeling
- Strong performance on tabular datasets
- Commonly used in industrial applications

# Model Performance and Results

The choice of model depends on the operational context.

The **Random Forest model** presented a more balanced performance and demonstrated better generalization across the dataset.

The **XGBoost model**, on the other hand, showed higher sensitivity in detecting mechanical faults, making it potentially more suitable for scenarios where **missing a failure is unacceptable**.

However, this increased sensitivity resulted in a significant number of **false positives in the "Normal" class**, which would not be ideal for a production environment.

Several preprocessing strategies were tested to mitigate this issue, but none produced fully satisfactory results.

As a result, the **Random Forest model stands out for its more balanced and generalized performance**, making it a stronger candidate for production use.

# Discussion

From my perspective, the **XGBoost model shows strong potential for detecting imbalance-related failures**, while the **Random Forest model performs more reliably when identifying the Normal class**.

In an ideal scenario, combining the strengths of both models could produce better results — leveraging the **fault detection sensitivity of XGBoost** together with the **stability of Random Forest for normal operation classification**.

The inconsistencies observed in XGBoost when predicting the "Normal" class may reflect limitations of the current modeling approach or feature representation. Further experimentation with preprocessing, feature engineering, and model tuning will be explored to improve its performance.
