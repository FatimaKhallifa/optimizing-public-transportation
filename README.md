# Optimizing Public Transportation
## Predicting Monthly Transit Ridership for Better Resource Planning
## Project Overview

This project aims to **predict monthly public transportation ridership** using historical data from the National Transit Database (NTD).
We analyze ridership trends, seasonality, COVID-19 impact, transportation modes, and operational factors such as Vehicle Revenue Hours (VRH) and Vehicle Revenue Miles (VRM).

Three forecasting models were developed and compared:
* Multiple Linear Regression
* Random Forest
* Auto-ARIMA

Based on the evaluation results, **Random Forest was selected as the final model** and used to forecast ridership for the next 12 months.

The main goal is to provide transportation agencies with data-driven insights that can support **better service planning, resource allocation, and future demand management**.

## Team Members
* Fatima Abuelazaim Khalifa
* Shamma Alsawwafi
* Huda Almashjari

## Project Objectives
The main objectives of this project are to:

* Analyze historical public transportation ridership trends.
* Identify monthly seasonality and changes in passenger demand.
* Analyze the impact of COVID-19 on public transit ridership.
* Examine the relationship between ridership and operational service metrics.
* Build and compare different forecasting models.
* Forecast monthly transit ridership for the next 12 months.
* Support transportation resource planning and data-driven decision-making.

## Dataset
The project uses monthly ridership data from the **National Transit Database (NTD)**.
The dataset contains transportation information including:
* `Date`
* `Agency`
* `State`
* `Mode`
* `TOS`
* `UPT` - Unlinked Passenger Trips
* `VRH` - Vehicle Revenue Hours
* `VRM` - Vehicle Revenue Miles
* `VOMS` - Vehicles Operated in Maximum Service

The original dataset contains monthly transportation data covering multiple years.

For the focused trend analysis, we used data from **2014 to Present** because this period provides a more relevant view of recent transportation patterns while also capturing the COVID-19 disruption and post-COVID recovery.

## Project Workflow
Data Loading
     |
Data Cleaning & Preprocessing
     |
Exploratory Data Analysis
     |
Feature Engineering
     |
Train/Test Split
     |
Model Building
     |
Model Evaluation
     |
Model Selection
     |
12-Month Future Forecast


## 1. Environment Setup
The analysis was implemented in **R using Google Colab**.
Main R packages used:
* `tidyverse`
* `lubridate`
* `janitor`
* `scales`
* `caret`
* `randomForest`
* `forecast`
* `corrplot`
* `zoo`

These packages were used for data manipulation, date processing, visualization, machine learning, correlation analysis, and time series forecasting.

## 2. Data Cleaning and Preprocessing
The raw dataset was cleaned and standardized before analysis.
The main preprocessing steps include:
* Standardizing column names using `janitor`.
* Mapping the main variables to consistent names.
* Converting dates into standard `Date` format.
* Converting ridership and operational variables into numeric values.
* Converting categorical variables such as agency, mode, TOS, and state into factors.
* Removing records with missing dates or missing ridership.
* Keeping records with positive ridership (`UPT > 0`).
* Removing duplicate records.

The cleaned dataset was exported as:
clean_ntd_monthly_ridership.csv
This file was used as the data source for the Power BI dashboard.

## 3. Exploratory Data Analysis
### Historical Ridership Trend
Monthly national ridership was aggregated by date using total UPT.
The analysis identified:
* Long-term changes in passenger demand.
* A major decline in ridership during COVID-19.
* A gradual recovery after the pandemic.
The COVID-19 impact was highlighted from March 2020.

### Monthly Seasonality
Average ridership was calculated for each month across the available years.
This analysis was used to identify monthly fluctuations and potential seasonal patterns, which are important for monthly ridership forecasting.

### Focused Trend Analysis
The project also focuses on the period from **2014 to Present**.
This period was selected because:
* It better represents recent transportation and passenger travel patterns.
* It includes the COVID-19 disruption.
* It captures the post-COVID recovery period.

### Ridership by Transportation Mode
Total ridership was aggregated by transportation mode to understand which modes contribute most to national passenger demand.

### Correlation Analysis
A correlation matrix was created to examine the relationships between:
* UPT
* VRH
* VRM
* VOMS

The analysis showed strong relationships between passenger demand and operational service metrics, supporting their use as forecasting features.

## 4. Feature Engineering
The project creates several time-based features for forecasting.
### Temporal Features
* `year`
* `month`
### Lag Features
* `lag_1`: Previous month's ridership.
* `lag_12`: Ridership from the same month in the previous year.
These features help capture short-term momentum and yearly seasonal patterns.

### Moving Average
A 3-month moving average was also calculated during feature preparation.
## 5. Train/Test Split
A chronological split was used instead of a random split because the project deals with time series data.
The **last 24 months** were reserved as the test set.
Training Data → Historical months
Test Data     → Last 24 months
This provides a more realistic evaluation of how the models perform on future, unseen data.

## 6. Forecasting Models
Three forecasting approaches were developed and compared.
### Multiple Linear Regression
Multiple Linear Regression was used as a baseline model.
Features:
lag_1
lag_12
total_vrh
total_vrm
month

### Random Forest
Random Forest was used to capture non-linear relationships between ridership, historical demand, seasonality, and operational variables.
Features:
lag_1
lag_12
total_vrh
total_vrm
month
year

The model was trained using:
ntree = 300
seed = 123


### Auto-ARIMA
Auto-ARIMA was used as a time series forecasting benchmark.
The model was trained on the monthly ridership time series with a frequency of 12 to capture annual seasonality.

## 7. Model Evaluation
The three models were evaluated on the 24-month test set using:
### MAE
**Mean Absolute Error** measures the average absolute difference between actual and predicted ridership.
### RMSE
**Root Mean Squared Error** gives more weight to larger prediction errors.
### MAPE
**Mean Absolute Percentage Error** measures prediction error as a percentage, making it easier to compare forecasting accuracy.
The evaluation results are stored in:
results_summary

Random Forest was selected as the final forecasting model because it achieved the **lowest overall error across the evaluated metrics**.

## 8. Prediction Comparison
The project compares:
* Actual ridership
* Linear Regression predictions
* Random Forest predictions
* Auto-ARIMA predictions
over the 24-month test period.
The comparison helps visually evaluate how closely each model follows the actual ridership pattern.

## 9. Future Ridership Forecast
After model evaluation, the Random Forest model was retrained using the available historical data.
The model was then used to forecast the **next 12 months** of monthly ridership.
For future forecasting, the model requires operational variables such as VRH and VRM. Since their future values are unknown, **historical monthly averages** were used as estimated future inputs.

The forecast also uses:
* Month
* Year
* Previous month's predicted ridership
* Previous year's ridership
* Estimated VRH
* Estimated VRM

The model predicts each future month sequentially, using previous predictions to generate the required `lag_1` values.

## 10. Final Output
The project produces:
* Cleaned transportation dataset.
* Historical ridership trend visualizations.
* Monthly seasonality analysis.
* Transportation mode analysis.
* Correlation matrix.
* Model evaluation results.
* Actual vs. predicted ridership comparison.
* Next 12-month ridership forecast.
* Historical vs. future forecast visualization.

## Business Value
The forecasting results can help transportation agencies:
* Estimate future passenger demand.
* Plan bus and transit services.
* Allocate transportation resources more efficiently.
* Reduce overcrowding and underutilization.
* Support data-driven operational decisions.
* Improve planning based on seasonal and historical demand patterns.

## Technologies Used

| Category             | Tools               |
| -------------------- | ------------------- |
| Programming          | R                   |
| Environment          | Google Colab        |
| Data Manipulation    | tidyverse, dplyr    |
| Data Cleaning        | janitor             |
| Date Processing      | lubridate           |
| Visualization        | ggplot2, scales     |
| Machine Learning     | randomForest, caret |
| Time Series          | forecast            |
| Correlation Analysis | corrplot            |
| Rolling Calculations | zoo                 |
| Dashboard            | Power BI            |

## Repository Structure
Optimizing-Public-Transportation/
│
├── data/
│   ├── Complete_Monthly_Ridership.csv
│   └── clean_ntd_monthly_ridership.csv
│
├── notebooks/
│   └── Optimizing_public_transportation_ZAKA_Capstone.ipynb
│
├── dashboard/
│   └── PowerBI_Dashboard.pbix
│
├── README.md
└── requirements.txt
```

## How to Run the Project

1. Open the notebook in Google Colab.
2. Upload the NTD monthly ridership dataset.
3. Run the library installation and loading section.
4. Run the data cleaning and preprocessing steps.
5. Run the exploratory data analysis.
6. Run the feature engineering section.
7. Train and evaluate the three forecasting models.
8. Compare the model performance.
9. Run the Random Forest future forecasting section.
10. Review the 12-month ridership forecast.

## Data Source
**National Transit Database (NTD)** monthly public transportation ridership data.

## Project Outcome
The project combines historical trend analysis, operational data, and machine learning to forecast monthly public transportation ridership.

After comparing **Multiple Linear Regression, Random Forest, and Auto-ARIMA**, Random Forest was selected based on its overall forecasting performance and was used to generate a **12-month future ridership forecast**.

The results can support transportation agencies in making more informed decisions about **service planning, resource allocation, and future passenger demand**.


##  Project Links & Resources
* 📓 **Google Colab Notebook:** https://colab.research.google.com/drive/162V8PdrdAaf3BUE6rGL7uoqSKJzMJARS?usp=drive_link
* 📊 **Power BI Dashboard:** https://app.powerbi.com/links/IpRLsnG_YE?ctid=55488759-d4c9-4a95-ae92-ada1488c4053&pbi_source=linkShare&bookmarkGuid=1667227a-493d-4d28-a54d-97767de5ba6f
* 📂 **Raw Dataset:** https://drive.google.com/file/d/1cSnK7KUUCt5t2yNQDJfpMA59XBrVFNhi/view?usp=sharing
* 📂 **Cleaned Dataset:** https://drive.google.com/file/d/16BT9v7Nh6OSDPiCQWJA-n2svXF-UeQlY/view?usp=sharing
