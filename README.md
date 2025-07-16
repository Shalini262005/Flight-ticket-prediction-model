
# ✈️ Flight Ticket Price Prediction

This project presents a machine learning pipeline to predict airline ticket prices based on flight details. The notebook processes real-world flight data and builds regression models to estimate the price of a ticket given various features like airline, source, destination, number of stops, travel class, and more.

## Dataset

The dataset is sourced from a Kaggle competition environment and contains the following:

- `train_data.csv`: Used to train and evaluate the model.
- `test_data.csv`: Used for final prediction without price labels.

### Features

- `airline`: Name of the airline.
- `flight`: Flight number.
- `source`, `destination`: City of departure and arrival.
- `departure`, `arrival`: Departure and arrival time (categorical time buckets).
- `stops`: Number of stops.
- `class`: Travel class (Economy/Business).
- `duration`: Total travel duration in hours.
- `days_left`: Days left until the journey.
- `price`: Target variable (only in training data).

## Exploratory Data Analysis (EDA)

- Checked data types and missing values.
- Verified distributions and outliers in features like `duration`, `days_left`, and `price`.
- Analyzed categorical variables using bar plots and value counts.

## Data Preprocessing

- **One-Hot Encoding**: Applied to `airline`, `source`, and `destination`.
- **Ordinal Encoding**:
  - `departure`, `arrival`: Time slots (e.g., Early_Morning → Late_Night)
  - `stops`: ['zero', 'one', 'two_or_more']
  - `class`: ['Economy', 'Business']
- **Scaling**: Numerical features standardized using `StandardScaler`.
- **Dropped**: `id` and `flight` as non-informative features.

## Model Building

Models used for regression:

- **Linear Regression**
- **Lasso Regression**
- **Ridge Regression**
- **ElasticNet Regression**
- **Decision Tree**
- **Random Forest Regressor**
- **Gradient Boosting Regressor**

## Model Evaluation

Metrics used:

- **R² Score on both train and test data**
- **Root Mean Squared Error (RMSE)**

Models were evaluated using cross-validation.

### Results Summary

#### Model Performance on Test Set

| Model                  | Test R² | Test RMSE |
|------------------------|---------|-----------|
| Linear Regression      | 0.9087  | 0.3380    |
| Ridge Regression       | 0.9087  | 0.3380    |
| Lasso Regression       | 0.8356  | 0.4535    |
| ElasticNet Regression  | 0.8271  | 0.4650    |
| Decision Tree          | 0.9434  | 0.2660    |
| Random Forest          | 0.9571  | 0.2317    |
| Gradient Boosting      | 0.9427  | 0.2677    |

#### Cross-Validation Performance Summary

| Model            | Best CV RMSE | Notes                                             |
|------------------|--------------|---------------------------------------------------|
| Random Forest    | 0.2293       | Best overall — low error, stable                  |
| Gradient Boosting| 0.2408       | Strong, slightly slower, better with tuning       |
| Decision Tree    | 0.2610       | Simpler, interpretable, slightly worse performance|


## Final Prediction

- The Random forest Regressor was selected as the final model for generating predictions on the `test.csv` data.
- Output predictions were stored in a CSV file.

## Conclusion

This project demonstrates how to build a complete machine learning pipeline — from preprocessing and feature engineering to model training and evaluation — to tackle a real-world regression problem using flight data.
