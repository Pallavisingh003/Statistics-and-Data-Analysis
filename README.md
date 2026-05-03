# SCHOOL OF COMPUTER SCIENCE

### University Of Petroleum And Studies.

 
 <img width="584" height="157" alt="Screenshot 2026-05-03 at 3 58 08 PM" src="https://github.com/user-attachments/assets/ebe4991a-410a-4f20-93bf-0b4ad1066314" />


### SEMESTER-06








Submitted By: Pallavi Singh
Sap Id:500119176
Roll no:R2142230249
SCHOOL: SOCS




# Statistics-and-Data-Analysis

# Introduction

This assignment focuses on two important areas of data analysis:

1. Principal Component Analysis (PCA) for dimensionality reduction and customer behavior analysis.
2. Time-Series Analysis and Forecasting using ARIMA models.

PCA was used to reduce the complexity of customer purchase data and better understand customer behavior patterns. Time-Series Analysis was used to study sales data over a period of time and predict future sales using the ARIMA forecasting model. The complete implementation was done using Python in Visual Studio Code on macOS. Several Python libraries such as pandas, numpy, matplotlib, seaborn, scikit-learn, and statsmodels were used for data preprocessing, visualization, analysis, and forecasting.

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

<img width="394" height="307" alt="Screenshot 2026-04-30 at 11 06 55 PM" src="https://github.com/user-attachments/assets/900a672d-1fc5-47d9-9668-78f9d51c9184" />



---

# Steps Performed

## Step 1: Load Dataset

The dataset was loaded using pandas.

```python
import pandas as pd

data = pd.read_csv("Mall_Customers.csv")
```

<img width="943" height="865" alt="Screenshot 2026-04-30 at 11 10 39 PM" src="https://github.com/user-attachments/assets/5b412cb9-b5da-4d52-8204-83c2865b83e3" />


---

## Step 2: Handle Missing Values

Missing values were replaced using the mean value.

```python
X = X.fillna(X.mean())
```

<img width="482" height="39" alt="Screenshot 2026-05-03 at 3 43 31 PM" src="https://github.com/user-attachments/assets/0b478a46-1f13-4dc2-a27d-e03fe00614a7" />

---

## Step 3: Normalize Features

Standardization was performed using StandardScaler.

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
```

<img width="352" height="56" alt="Screenshot 2026-05-03 at 3 43 58 PM" src="https://github.com/user-attachments/assets/2420b566-3907-46ee-a3cd-565577d54eeb" />


---

## Step 4: Apply PCA

PCA was applied to reduce dimensions.

```python
from sklearn.decomposition import PCA

pca = PCA()
pca_data = pca.fit_transform(X_scaled)
```

<img width="367" height="67" alt="Screenshot 2026-05-03 at 3 44 08 PM" src="https://github.com/user-attachments/assets/916564dd-44e9-4245-b3f3-6543b9e3d8da" />


---

## Step 5: Determine Explained Variance

The explained variance ratio was calculated.

```python
explained_variance = pca.explained_variance_ratio_
```

<img width="420" height="163" alt="Screenshot 2026-05-03 at 3 44 28 PM" src="https://github.com/user-attachments/assets/a3459e2d-7f21-4eae-bdf7-86c765d70a69" />


---

## Step 6: Visualization

Two graphs were generated:

1. Explained Variance Graph
2. 2D PCA Scatter Plot


<img width="601" height="23" alt="Screenshot 2026-05-03 at 3 19 47 PM" src="https://github.com/user-attachments/assets/f7991fa0-7b78-4d5c-92ec-fba306d6a3b4" />


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

<img width="639" height="533" alt="Screenshot 2026-05-03 at 3 19 35 PM" src="https://github.com/user-attachments/assets/334026cf-3449-400d-8939-0790ad5c8645" />


<img width="632" height="536" alt="Screenshot 2026-05-03 at 3 19 59 PM" src="https://github.com/user-attachments/assets/787606fd-315a-4799-b23c-fb8a5bd03c44" />


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

<img width="947" height="604" alt="Screenshot 2026-04-30 at 11 10 51 PM" src="https://github.com/user-attachments/assets/abae0d36-aa02-46ff-857d-76065c2c9565" />


---

# Steps Performed

## Step 1: Load Dataset

```python
import pandas as pd

data = pd.read_csv("sales_data.csv")
```

<img width="266" height="44" alt="Screenshot 2026-05-03 at 3 46 29 PM" src="https://github.com/user-attachments/assets/35b30206-ebad-4a66-aff7-3ec007dec657" />


---

## Step 2: Convert Date Column

```python
data['Date'] = pd.to_datetime(data['Date'])
```

<img width="331" height="59" alt="Screenshot 2026-05-03 at 3 46 37 PM" src="https://github.com/user-attachments/assets/2e3eff40-6bfc-4dc6-be27-c60826bc3c47" />


---

## Step 3: Set Date as Index

```python
data.set_index('Date', inplace=True)
```

<img width="285" height="41" alt="Screenshot 2026-05-03 at 3 46 53 PM" src="https://github.com/user-attachments/assets/07051344-9893-461f-871f-e858fba6976d" />


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

<img width="551" height="89" alt="Screenshot 2026-05-03 at 3 48 46 PM" src="https://github.com/user-attachments/assets/9fa2bcf3-6075-4222-bf77-ff02998a4bda" />

---

## Step 7: Perform ADF Test

The Augmented Dickey-Fuller test was performed.

```python
from statsmodels.tsa.stattools import adfuller
```

<img width="268" height="64" alt="Screenshot 2026-05-03 at 3 49 04 PM" src="https://github.com/user-attachments/assets/d7e524b4-7c31-4c07-9f18-9187ed5bf510" />

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

<img width="616" height="33" alt="Screenshot 2026-05-03 at 3 20 21 PM" src="https://github.com/user-attachments/assets/e51ca4b8-1988-4702-b6c1-388060433c00" />


Interpretation:

Lower MAE and RMSE values indicate better forecasting performance.

---

# Output Obtained

## Time-Series Plot

The graph showed:

* Increasing sales trend over time
* Seasonal patterns
* Daily fluctuations

<img width="633" height="534" alt="Screenshot 2026-05-03 at 3 20 27 PM" src="https://github.com/user-attachments/assets/13056e63-3008-4829-8786-a1cef2802b07" />

<img width="637" height="532" alt="Screenshot 2026-05-03 at 3 20 35 PM" src="https://github.com/user-attachments/assets/76bee0fc-d84d-4b12-b4d9-8960306cd0a6" />


---

# Final Conclusion

This assignment helped in understanding how data analysis and forecasting techniques work in real-life situations. Using PCA, the customer purchase data was simplified so that customer behavior and spending patterns could be understood more easily through graphs and visualizations. In the time-series part, sales data was analyzed to observe trends, seasonal changes, and future sales predictions using the ARIMA model. Different Python libraries like pandas, matplotlib, scikit-learn, and statsmodels were used to clean the data, create graphs, and build prediction models. Overall, this assignment gave practical knowledge of data analysis and forecasting in a simple and hands-on way.

---
