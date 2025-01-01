# Flight-Ticket-Price-Prediction

### Introduction
Flight ticket prices can be unpredictable. One day, you might see a specific fare, and the next day, it could be a completely different story. Travelers often mention how hard it is to guess when to buy tickets. As data scientists, we take on the challenge to prove that with the right data, anything can be predicted.

In this project, we'll use flight ticket prices for various airlines between March and June 2019, across multiple cities, to predict the ticket prices. With machine learning models, we aim to make flight prices more predictable and understandable.

### Dataset Overview
Training set size: 10,683 records
Test set size: 2,671 records
Time period: March to June 2019
Data Includes: Airlines, flight routes, duration, stops, and ticket prices.

### The dataset includes the following features:

* Airline: The name of the airline (e.g., Indigo, Jet Airways).
* Date_of_Journey: The date on which the journey takes place.
* Source: The departure city.
* Destination: The arrival city.
* Route: The route taken by the flight, including stopovers.
* Dep_Time: The departure time from the source.
* Arrival_Time: The arrival time at the destination.
* Duration: The total duration of the flight.
* Total_Stops: The number of stops between source and destination.
* Additional_Info: Additional information about the flight (e.g., "No info", "In-flight meal not included").
* Price: The price of the ticket (Target variable).

### Inferences and Key Observations
Through Exploratory Data Analysis (EDA), we found several key insights:

* Most Frequent Airline: Jet Airways has the most flights in the dataset.
* Source and Destination: Delhi is the most frequent source, and Cochin is the most common destination.
* Frequent Routes: The route DEL → BOM → COK is the most frequent.
* Stops: Most flights have 1 stop.
* Data Cleanup: Some categories needed cleaning, such as duplicate categories for "Delhi" and "New Delhi" and inconsistencies in "Additional_Info."

### Project Workflow
* Loading the Data: Loaded the necessary libraries and datasets.
* Exploratory Data Analysis (EDA): Analyzed and visualized the data to understand key patterns.
* Data Preprocessing: Cleaned and processed the dataset to handle missing values and inconsistent categories.
* Feature Engineering: Created new features from existing data to improve model performance.
* Modeling: Applied various machine learning models to predict flight prices.

### Data Preprocessing
* Handling Missing Data: Filled missing values for the "Price" "Route" and "Total Stops" columns.
* Duplicate Categories: Cleaned up duplicate categories like "Delhi" and "New Delhi" and standardized the "Additional_Info" column.
* Encoding: Used frequency encoding for categorical variables.

### Feature Engineering
* Date-Based Features: Extracted day, month, and weekday from the "Date_of_Journey" column.
* Time-Based Features: Split Dep_Time and Arrival_Time into separate hour and minute components.
* Duration: Converted the "Duration" feature into numerical hours for consistency.

### Predictive Modeling
We tested multiple machine learning models to predict flight ticket prices:

* Models Evaluated:
               
LinearRegression, Ridge(alpha=1), Lasso(alpha=1), DecisionTreeRegressor(max_depth=9), RandomForestRegressor(max_depth=10), GradientBoostingRegressor(max_depth=7), XGBRegressor()	

### Final Model: Stacking Regressor
To improve performance, we used a Stacking Regressor that combines predictions from multiple models:

- Models in the Stacking Regressor:
  * Decision Tree Regressor (DT1)
  * Random Forest Regressor (RF1)
  * Gradient Boosting Regressor (GBR)
  * XGBoost Regressor (XGBR)
The final predictions were aggregated using RidgeCV.

* Performance of the Stacking Regressor:
Metric	Value
R²	0.8827
MSE	2,609,088
RMSE	1,615.26
MAPE	0.08%
The Stacking Regressor provided the best results, demonstrating the power of combining models for improved accuracy.

### Results
The Stacking Regressor proved to be the most accurate model for predicting flight ticket prices. With an R² of 0.8827 and a low RMSE of 1,615.26, it significantly outperformed simpler models like linear regression.

### Conclusion
This project demonstrates how machine learning can be applied to predict flight ticket prices with a high degree of accuracy. By carefully cleaning and processing the data, performing feature engineering, and using advanced ensemble models like Stacking, we were able to make meaningful predictions about flight prices.
