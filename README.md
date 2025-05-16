# Time-Series-Forecasting-Project

**Author**: Elvessa Tatum

## Problem Statement

The objective of this project is to forecast retail sales using historical sales data. Accurate sales predictions help businesses manage inventory, staffing, and financial planning. We aim to develop time series models that can capture seasonality, trends, and other temporal patterns in the data to predict future sales effectively.

---

## About the Data

The dataset is sourced from the [Kaggle Store Sales - Time Series Forecasting](https://www.kaggle.com/competitions/store-sales-time-series-forecasting/data) competition. It contains historical daily sales data for multiple stores and product families in Ecuador.

- **Rows**: ~3 million
- **Columns**:
  - `date`: Date of the sale
  - `store_nbr`: Store number
  - `family`: Product category
  - `sales`: Number of items sold
  - `onpromotion`: Items on promotion

---

## Project Structure

### **1. Data Preparation**

- Checked for missing values (none found)
- Created time-based features: year, month, day of the week
- Visualized sales trends over time, by month, and by weekday
- Split data into train and test sets using a cutoff date (`2017-01-01`)

### **2. Model Development**

- **SARIMA Model**:
  - Used seasonal and trend components
  - Fit using `SARIMAX` from `statsmodels`
- **Prophet Model**:
  - Facebook’s time series forecasting tool
  - Automatically handles holidays, seasonality, and trends
- **Moving Average**:
  - 7-day simple moving average for baseline comparison

### **3. Evaluation**

Metrics used:

- RMSE (Root Mean Squared Error)
- MAE (Mean Absolute Error)
- MAPE (Mean Absolute Percentage Error)

| Model   | RMSE            | MAE        | MAPE (%) |
| ------- | --------------- | ---------- | -------- |
| SARIMA  | 187,864,310,677 | 404,867.84 | 94.98%   |
| Prophet | 22,334,269,406  | 96,327.97  | 49.22%   |

Residuals and actual vs predicted plots were generated for both models.

---

## Conclusion

- **Prophet** significantly outperformed **SARIMA** across all evaluation metrics.
- SARIMA struggled with capturing complex patterns and had much higher error rates.
- Prophet’s built-in handling of trend and seasonal components proved more effective for this retail dataset.
- Both models showed clear patterns in weekly seasonality, supporting the business relevance of temporal sales trends.

---

## Files Included

- `train.csv`: Raw sales data
- `notebook.ipynb`: Full code and visualizations
- `README.md`: Project overview and summary

---

## Future Work

- Incorporate external regressors like promotions and holidays
- Try more advanced models like LSTM or XGBoost with time features
- Perform hyperparameter tuning for SARIMA and Prophet

