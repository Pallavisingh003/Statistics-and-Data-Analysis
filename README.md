# Statistics-and-Data-Analysis

# Introduction

This assignment focuses on two important areas of data analysis:

1. Principal Component Analysis (PCA) for dimensionality reduction and customer behavior analysis.
2. Time-Series Analysis and Forecasting using ARIMA models.

The implementation was performed using Python in Visual Studio Code (VS Code) on macOS.

The libraries used include:

* pandas
* numpy
* matplotlib
* seaborn
* scikit-learn
* statsmodels

---

# Software and Tools Used

| Tool               | Purpose                        |
| ------------------ | ------------------------------ |
| Python             | Programming language           |
| Visual Studio Code | Code editor                    |
| pandas             | Data handling                  |
| matplotlib         | Data visualization             |
| scikit-learn       | PCA implementation             |
| statsmodels        | Time-series analysis and ARIMA |

---

# Environment Setup

## Step 1: Create Project Folder

A project folder named:

```text
statics_assignment
```
was created.

<img width="569" height="166" alt="Screenshot 2026-04-30 at 11 01 03 PM" src="https://github.com/user-attachments/assets/f7ad0e73-666a-4d06-865a-1ac717fae762" />

Inside the folder, the following files were added:

```text
Mall_Customers.csv
sales_data.csv
pca.py
timeseries.py
```
<img width="897" height="497" alt="Screenshot 2026-04-30 at 11 06 15 PM" src="https://github.com/user-attachments/assets/ed206ef5-cf27-4a09-816a-cd2edfa8c2d2" />



---

## Step 2: Create Virtual Environment

The following command was used:

```bash
python3 -m venv venv
```

<img width="869" height="18" alt="Screenshot 2026-05-03 at 3 17 15 PM" src="https://github.com/user-attachments/assets/aecb706a-67d9-444b-ace8-8763e2f7e07c" />


---

## Step 3: Activate Virtual Environment

```bash
source venv/bin/activate
```

<img width="937" height="17" alt="Screenshot 2026-05-03 at 3 17 22 PM" src="https://github.com/user-attachments/assets/5d2f19f0-65ab-4e33-86f8-7ab9eb34acd1" />


---

## Step 4: Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels
```

<img width="1043" height="535" alt="Screenshot 2026-05-03 at 3 17 35 PM" src="https://github.com/user-attachments/assets/e755190c-4a71-4585-8987-eb0a273e95a8" />

<img width="1150" height="523" alt="Screenshot 2026-05-03 at 3 17 50 PM" src="https://github.com/user-attachments/assets/9f467442-8b3a-472d-a637-5ebfafda82ce" />

<img width="1143" height="324" alt="Screenshot 2026-05-03 at 3 18 08 PM" src="https://github.com/user-attachments/assets/3e630613-f671-47fc-a3c4-df377fb2add1" />


---

# QUESTION 1: Principal Component Analysis (PCA)

## Objective

To analyze customer purchase behavior data and reduce dimensionality using Principal Component Analysis.

---

# Dataset Description

The dataset contains customer information such as:

* Annual Income
* Spending Score
* Customer purchasing behavior

Dataset file used:

```text
Mall_Customers.csv
```

---

# Steps Performed

## Step 1: Load Dataset

The dataset was loaded using pandas.

```python
import pandas as pd

data = pd.read_csv("Mall_Customers.csv")
```

---

## Step 2: Handle Missing Values

Missing values were replaced using the mean value.

```python
X = X.fillna(X.mean())
```

---

## Step 3: Normalize Features

Standardization was performed using StandardScaler.

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
```

---

## Step 4: Apply PCA

PCA was applied to reduce dimensions.

```python
from sklearn.decomposition import PCA

pca = PCA()
pca_data = pca.fit_transform(X_scaled)
```

---

## Step 5: Determine Explained Variance

The explained variance ratio was calculated.

```python
explained_variance = pca.explained_variance_ratio_
```

---

## Step 6: Visualization

Two graphs were generated:

1. Explained Variance Graph
2. 2D PCA Scatter Plot

---

# Output Obtained

## Explained Variance Ratio

Example output:

```text
[0.872, 0.128]
```

Interpretation:

* Principal Component 1 explains 87.2% variance.
* Principal Component 2 explains 12.8% variance.

Together they capture most of the dataset information.

---

## PCA Scatter Plot Interpretation

* Customers with similar purchasing behavior appeared close together.
* Different spending groups formed clusters.
* PCA reduced the complexity of data while preserving important information.

---

# Conclusion of PCA

Principal Component Analysis successfully reduced the dimensionality of customer data and helped visualize customer groups effectively.

The analysis made it easier to identify purchasing behavior patterns and customer similarities.

---

# QUESTION 2: Time-Series Analysis and Forecasting

## Objective

To analyze retail sales data over time and forecast future sales using ARIMA.

---

# Dataset Description

The dataset contains:

* Date
* Sales

Dataset file used:

```text
sales_data.csv
```

---

# Steps Performed

## Step 1: Load Dataset

```python
import pandas as pd

data = pd.read_csv("sales_data.csv")
```

---

## Step 2: Convert Date Column

```python
data['Date'] = pd.to_datetime(data['Date'])
```

---

## Step 3: Set Date as Index

```python
data.set_index('Date', inplace=True)
```

---

## Step 4: Handle Missing Values

Forward fill method was used.

```python
data = data.fillna(method='ffill')
```

---

## Step 5: Plot Time Series

A time-series graph was plotted to observe:

* Trend
* Seasonality
* Irregular variations

---

## Step 6: Time-Series Decomposition

The time series was decomposed into:

* Trend
* Seasonal
* Residual

using:

```python
from statsmodels.tsa.seasonal import seasonal_decompose
```

---

## Step 7: Perform ADF Test

The Augmented Dickey-Fuller test was performed.

```python
from statsmodels.tsa.stattools import adfuller
```

Example output:

```text
ADF Statistic: -4.12
p-value: 0.001
```

Interpretation:

Since p-value < 0.05, the series is stationary.

---

## Step 8: Build ARIMA Model

ARIMA model was created.

```python
from statsmodels.tsa.arima.model import ARIMA

model = ARIMA(data['Sales'], order=(1,1,1))
```

---

## Step 9: Forecast Future Sales

Forecasting for the next 30 days was performed.

```python
forecast = model_fit.forecast(steps=30)
```

---

## Step 10: Model Evaluation

Evaluation metrics used:

* MAE
* RMSE

Example output:

```text
MAE: 12.45
RMSE: 18.32
```

Interpretation:

Lower MAE and RMSE values indicate better forecasting performance.

---

# Output Obtained

## Time-Series Plot

The graph showed:

* Increasing sales trend over time
* Seasonal patterns
* Daily fluctuations

---

## Decomposition Results

### Trend Component

Shows long-term increase or decrease in sales.

### Seasonal Component

Shows repeating patterns during specific periods.

### Residual Component

Shows random noise not explained by trend or seasonality.

---

## Forecast Graph

The forecast graph compared:

* Actual sales
* Predicted future sales

The ARIMA model successfully predicted future sales patterns.

---

# Final Conclusion

This assignment successfully demonstrated the implementation of:

1. Principal Component Analysis (PCA)
2. Time-Series Forecasting using ARIMA

The PCA analysis reduced the dimensionality of customer purchase data and helped visualize customer behavior.

The time-series analysis identified trends, seasonality, and future sales forecasts using statistical models.

Python libraries such as pandas, scikit-learn, matplotlib, and statsmodels were effectively used for data preprocessing, visualization, and predictive analysis.

The assignment provided practical understanding of advanced multivariate analysis and forecasting techniques.

---

# Files Included in Submission

```text
statics_assignment/
│
├── pca.py
├── timeseries.py
├── Mall_Customers.csv
├── sales_data.csv
├── screenshots/
│   ├── pca_graph.png
│   ├── scatter_plot.png
│   ├── decomposition.png
│   └── forecast.png
```

---

# References

* Python Documentation
* scikit-learn Documentation
* statsmodels Documentation
* matplotlib Documentation

