# 🗽 NYC Taxi Trip Duration Prediction 🚖

This project aims to predict the **duration of taxi trips** in New York City using supervised machine learning techniques. The dataset contains historical trip records including timestamps, geographic coordinates, passenger count, and vendor information.

---

## 📁 Dataset Description

The dataset includes the following features:

- `pickup_datetime` / `dropoff_datetime`
- `pickup_longitude` / `pickup_latitude`
- `dropoff_longitude` / `dropoff_latitude`
- `passenger_count`
- `vendor_id`
- `store_and_fwd_flag`
- `trip_duration` *(Target Variable)*

---

## ⚙️ Data Preprocessing

### ✅ Feature Engineering:
- Extracted **hour, day, weekday, and month** from `pickup_datetime`
- Calculated **Haversine distance** (in km) between pickup and dropoff coordinates
- Applied **IQR clipping** to remove outliers
- Handled missing/null values

### ✅ Categorical Encoding:
- Applied **One-Hot Encoding** to `store_and_fwd_flag`

---

## 📊 Feature Selection

Selected features based on correlation, domain knowledge, and model performance:
- `passenger_count`
- `pickup_hour`, `pickup_day`, `pickup_month`
- `distance_km` *(engineered using geolocation)*
- `vendor_id`

---

## 🤖 Models Used

| Model                    | MAE   | RMSE  | R² Score | Adjusted R² |
|-------------------------|-------|-------|----------|-------------|
| Linear Regression        | 244   | 325   | 0.62     | 0.62        |
| Random Forest Regressor  | 223   | 305   | 0.67     | 0.67        |
| KNeighbors Regressor     | 225   | 310   | 0.66     | 0.66        |

---

## 🧪 Model Tuning

- Applied **GridSearchCV** for hyperparameter tuning (e.g., `fit_intercept` in Linear Regression)
- Used **5-Fold Cross Validation** to ensure generalization and avoid overfitting

---

## 📈 Evaluation Metrics

The following metrics were used to assess performance:
- **MAE** (Mean Absolute Error)
- **MSE** (Mean Squared Error)
- **RMSE** (Root Mean Squared Error)
- **R² Score**
- **Adjusted R² Score**

These metrics directly relate to how accurately and consistently the model can predict real-world trip durations — important for improving efficiency, resource allocation, and customer satisfaction.

---

## 📌 Final Model

After comparison, **Random Forest Regressor** was selected as the final model due to:
- Highest **R² Score**
- Lower **MAE/RMSE**
- Robustness to outliers
- Non-linearity handling

---

## 📉 Visualizations

- Actual vs Predicted Graphs
- Correlation heatmaps
- Feature importance charts using SHAP (optional)

---

## ✅ Conclusion

With proper feature engineering and model tuning, we achieved strong predictive performance. This solution can help taxi operators optimize pricing, ETA estimation, and fleet management.

---

## 📦 Requirements

```bash
pip install pandas numpy matplotlib scikit-learn
