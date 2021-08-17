# A Fine Windy Day - Power Prediction (HackerEarth)
This notebook is created as part of a [HackerEarth competition](https://www.hackerearth.com/problem/machine-learning/predict-the-power-kwh-produced-from-the-windmills-8-f055f832/). The goal is to predict wind turbine power generation in kW/h based on various provided features like temperature, wind direction, turbine status, weather, blade length, etc.

For this purpose, the data is explored and prepared and several algorithms (Linear, Random Forest, Gradient Boosting Tree, and Extreme Gradient Boosting) are optimized using GridSearchCV and RFECV. This has resulted in a final score of 96.3% (100 * R-squared).

## 1. Data Understanding
The distribution of the target feature 'windmill_generated_power(kW/h)' is visualized by plotting a histogram (below). It shows that the distribution is right skewed. In the notebook this skewness is (partially) removed. As a result, the eventual predictive performance of the machine learning models improved.

![distribution_target_value](https://user-images.githubusercontent.com/70854452/128375859-3a2a9f1b-d5ad-41da-8573-e6ea13aa6774.png)

Furthermore, a correlation matrix is plotted to look into the relation between numerical + target features. What stands out are the relatively high correlations between the target feature and the features: 'motor_torque(N-m)' (0.51), 'generator_temperature(°C)' (0.39), and 'wind_direction(°)' (0.36). 

In addition, 'motor_torque(N-m)' and 'generator_temperature(°C)' are strongly correlated (0.93).

![correlation_matrix](https://user-images.githubusercontent.com/70854452/128377632-ae43853d-afc2-4e49-a498-6794a2efbd52.png)

The data is also checked for missing values. The bar plot below shows that for several features, but especially for 'blade_length(m)', 'atmospheric_temperature(°C)', 'atmospheric_pressure(Pascal)', and 'windmill_body_temperature(°C)' there is quite some data missing.

![missing_data](https://user-images.githubusercontent.com/70854452/128378686-e614451d-95ed-4194-affb-a9cc64e357a3.png)

Subsequently, potential outliers in the numerical features are flagged. To exemplify this, the scatter plot below is shown. In this plot a value with a z-score of 3 or more is colored red.

![potential_outliers](https://user-images.githubusercontent.com/70854452/128378974-e276ecfb-fcf1-43b1-94cf-0408fae542f6.png)

## 2. Data Preparation
Next, the following steps are taken to prepare the data:
- Remove outliers
- Encoding
- Feature engineering
- Fill missing data
- Reformat & Standardize

## 3. Modeling
Each algorithm is optimized/evaluated using:
- Hyper parameter optimization 
- K-fold cross validation (r2 score)

In addition, learning curves are created to determine whether over- or underfitting occurred.

![learning_curves](https://user-images.githubusercontent.com/70854452/129582842-144c4cd4-bbe1-4f60-8838-3c979a1b58c2.png)

And recursive feature elimination is applied:

![recursive_feature_elimination](https://user-images.githubusercontent.com/70854452/129580019-4bb0a2dc-12c9-45d6-b423-857a95bd2ef2.png)

In the end, it turned out that the Extreme Gradient Boosting algorithm resulted in the best prediction.