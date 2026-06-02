# Hotel Booking Cancellation Prediction Using Predictive Analytics

## Project Overview

Hotel booking cancellations significantly impact revenue forecasting, occupancy planning, staffing, and overall operational efficiency in the hospitality industry. This project uses predictive analytics and machine learning to identify reservations that are likely to be canceled before the arrival date.

The project explores customer booking behavior, performs extensive data preprocessing and feature engineering, and develops classification models to predict cancellation risk accurately.

---

## Project Objectives

* Analyze customer and booking data to identify cancellation patterns.
* Perform Exploratory Data Analysis (EDA) to uncover key trends.
* Clean and preprocess raw data.
* Engineer meaningful features to improve predictive performance.
* Build machine learning models for cancellation prediction.
* Generate actionable business insights to support hotel operations.

---

## Dataset Description

The dataset contains hotel reservation records, customer information, and stay characteristics.

### Key Features

| Feature                        | Description                                |
| ------------------------------ | ------------------------------------------ |
| lead_time                      | Days between booking date and arrival date |
| adults, children, babies       | Guest composition                          |
| stays_in_weekend_nights        | Weekend stay duration                      |
| stays_in_week_nights           | Weekday stay duration                      |
| previous_cancellations         | Customer's historical cancellations        |
| previous_bookings_not_canceled | Successful previous bookings               |
| adr                            | Average Daily Rate                         |
| total_of_special_requests      | Number of guest requests                   |

### Target Variable

| Value | Meaning              |
| ----- | -------------------- |
| 0     | Booking Not Canceled |
| 1     | Booking Canceled     |

---

## Project Workflow

### Day 1 — Exploratory Data Analysis (EDA)

* Examined dataset structure (119,390 rows × 32 columns).
* Identified missing values and data quality issues.
* Generated descriptive statistics.
* Detected outliers in variables such as ADR and Lead Time.
* Explored relationships between booking characteristics and cancellation behavior.

### Day 2 — Data Cleaning & Preprocessing

* Removed the `company` feature due to excessive missing values (94.3%).
* Filled missing values in `agent` with 0.
* Replaced missing countries with `"Unknown"`.
* Removed duplicate records.
* Converted date columns into appropriate datetime format.
* Applied one-hot encoding to categorical variables.

### Day 3 — Feature Engineering

Several new features were created:

#### Total Guests

```python
adults + children + babies
```

#### Total Nights

```python
stays_in_weekend_nights + stays_in_week_nights
```

#### Family Booking Indicator

```python
1 if children > 0 or babies > 0 else 0
```

#### Customer History

```python
previous_cancellations + previous_bookings_not_canceled
```

### Day 4 — Model Building

To avoid data leakage, booking outcome-related variables such as `reservation_status` were removed before training.

Models trained:

1. Logistic Regression
2. Decision Tree Classifier (Max Depth = 5)

Evaluation Metrics:

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix

### Day 5 — Insights & Recommendations

* Analyzed model performance.
* Identified major cancellation drivers.
* Generated operational recommendations for hotels.

---

## Model Performance

| Metric    | Logistic Regression | Decision Tree |
| --------- | ------------------- | ------------- |
| Accuracy  | 78.47%              | 79.45%        |
| Precision | 67.74%              | 68.07%        |
| Recall    | 36.83%              | 43.26%        |
| F1 Score  | 0.4772              | 0.5290        |

### Best Performing Model

✅ **Decision Tree Classifier**

The Decision Tree outperformed Logistic Regression across all evaluation metrics and captured more cancellation cases due to its ability to model non-linear relationships.

---

## Key Insights

### Reservation Lead Time Matters

Bookings made far in advance are more likely to be canceled.

### Stay Duration Impacts Risk

Longer stays tend to have higher cancellation probabilities.

### Family and Leisure Travelers Behave Differently

Family bookings show different cancellation patterns compared to business travelers.

### Customer History Is Highly Predictive

Customers with previous cancellations exhibit higher cancellation risk.

### Hotel Type Influences Cancellation Rate

City Hotels experience significantly higher cancellation rates compared to Resort Hotels.

### Non-Linear Models Capture Behavior Better

Decision Trees successfully modeled complex customer interactions that Logistic Regression struggled to learn.

---

## Business Recommendations

### 1. Proactively Engage High-Risk Guests

Contact guests predicted as high-risk before arrival through personalized communication.

### 2. Introduce Smart Deposit Policies

Require deposits for:

* Long lead-time bookings
* Extended stays
* Historically high-risk customer segments

### 3. Optimize Dynamic Overbooking

Use predicted cancellation probabilities to reduce revenue loss caused by empty rooms.

### 4. Strengthen Customer Loyalty Programs

Offer benefits to repeat customers while applying stricter verification for new customers.

### 5. Improve Operational Planning

Use cancellation forecasts to adjust:

* Staffing
* Inventory
* Procurement
* Room allocation

### 6. Continuously Retrain Models

Regularly update the model using fresh booking data to maintain prediction quality.

---

## Tools & Technologies

### Programming Language

* Python

### Libraries

* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn

### Development Environment

* Jupyter Notebook

---

## Future Improvements

### Advanced Ensemble Models

* Random Forest
* Gradient Boosting
* XGBoost

### Hyperparameter Optimization

* Grid Search
* Random Search

### Additional Features

* Weather information
* Seasonal demand indicators
* Customer satisfaction scores
* Travel cost trends

### Cross-Validation

Implement K-Fold Cross Validation for more robust model evaluation.

---

## Repository Structure

```text
Hotel-Booking-Cancellation-Prediction/
│
├── data/
├── notebooks/
├── images/
├── README.md
├── requirements.txt
└── model.pkl
```

---

## Author

**RIDHAN KM**

Data Analytics Intern | Machine Learning Enthusiast

Passionate about transforming data into actionable business insights through analytics and predictive modeling.
