# Zomato-Restaurant-Rating-Prediction
Capstone project using Zomato restaurant data to clean, analyze, and build regression models for predicting customer ratings. Includes EDA, feature engineering, and multiple machine learning models.

This project was developed as part of a capstone assignment, combining real-world data challenges with analytical insights and machine learning techniques.

## Business Problem

Zomato, a popular restaurant aggregator and food delivery platform, collects user ratings, costs, cuisine types, and various other data points from thousands of restaurants.

The goal of this project is to:
- Identify the most important factors that influence a restaurant’s customer rating.
- Build machine learning models to predict restaurant ratings accurately.
- Use data-driven insights to enhance visibility, pricing, and recommendation strategies.

## Dataset Overview

- **Dataset**: `Zomato Restaurants Dataset export 2025-07-07.csv`
- **Rows**: ~51,000+
- **Original Columns**: 12
- **Final Columns (after encoding)**: 60+
- **Target Variable**: `rate_(out_of_5)`

### Key Columns
- restaurant_name
- online_order
- table_booking
- rate_(out_of_5)
- avg_cost_(two_people)
- num_of_ratings
- local_address
- area
- cuisines_type
- restaurant_type

## Project Files

| File Name                                     | Description                                                     |
|----------------------------------------------|-----------------------------------------------------------------|
| `Zomato Restaurants Dataset export 2025.csv` | Raw Zomato restaurant data                                      |
| `Zomato Restaurant Preprocessing.ipynb`      | Contains full preprocessing steps and exploratory data analysis |
| `Zomato Restaurant (Machine Learning).ipynb` | Includes preprocessing and machine learning models              |

## Step-by-Step Workflow

### 1. Data Preprocessing
Performed in `Zomato Restaurant Preprocessing.ipynb`

- Removed duplicate rows and irrelevant columns (e.g., unnamed index columns)
- Renamed columns to lowercase with underscores for consistency
- Cleaned special characters from `restaurant_name`
- Converted `rate_(out_of_5)` to numeric and handled invalid entries like 'NEW' and '-'
- Cleaned and converted `avg_cost_(two_people)` to float
- Removed outliers using top and bottom 1% quantile filtering
- Applied `log1p` transformation to cost for normalization
- Encoded categorical columns:
  - Label Encoding: `online_order`, `table_booking`
  - One-Hot Encoding: `restaurant_type`, `cuisines_type`, `area`

### 2. Exploratory Data Analysis (EDA)

- Analyzed distributions of ratings, cost, and number of ratings
- Correlation heatmap to identify relationships
- Scatter plots of cost vs rating, and num_of_ratings vs rating
- Identified top 10 most popular areas
- Filtered high-rating, low-cost restaurant segments

### 3. Machine Learning
Performed in `Zomato Restaurant (Machine Learning).ipynb`

#### Train-Test Split
- Separated features (`X`) and target (`y`)
- Dropped unnecessary columns like `restaurant_name` and `local_address`
- Used 80-20 split for training and testing

#### Models Implemented
- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- Gradient Boosting Regressor
- Support Vector Regressor (SVR)

#### Evaluation Metrics
Each model was evaluated using:
- R² Score
- Mean Squared Error (MSE)
- Mean Absolute Error (MAE)

#### Results Summary

| Model                    | R² Score | MSE        | MAE     |
|-------------------------|----------|------------|---------|
| Linear Regression       | ~0.67    | Moderate   | Moderate|
| Decision Tree           | ~0.91    | Low        | Low     |
| Random Forest           | ~0.95+   | Lowest     | Best    |
| Gradient Boosting       | ~0.94    | Very Low   | Very Low|
| SVR                     | ~0.89    | Slightly higher | Competitive |

## Key Features Impacting Ratings

- num_of_ratings
- cost and log_cost
- Categorical variables from one-hot encoding (e.g., area, cuisines_type, restaurant_type)
- online_order and table_booking

## Future Scope

- Add hyperparameter tuning (e.g., GridSearchCV) to improve accuracy further
- Create a restaurant recommendation engine
- Deploy the model as a web app using Flask or Streamlit
- Integrate with live data from the Zomato API if available

## Conclusion

This capstone project demonstrates a complete data science workflow:
- Data cleaning and preprocessing
- Exploratory data analysis
- Feature engineering and transformation
- Regression modeling and evaluation




