# A Fine Windy Day - Power Prediction (HackerEarth)
This notebook is created as part of a [HackerEarth competition](https://www.hackerearth.com/problem/machine-learning/predict-the-power-kwh-produced-from-the-windmills-8-f055f832/). The goal is to predict wind turbine power generation in kW/h based on various provided features like temperature, wind direction, turbine status, weather, blade length, etc.

For this purpose, the data is explored and prepared and several algorithms (Linear, Random Forest, Gradient Boosting Tree, and Extreme Gradient Boosting) are optimized using GridSearchCV and RFECV. This has resulted in a final score of 96.3% (100 * R-squared).

## 1. Data Understanding

The distribution of the target feature 'windmill_generated_power(kW/h)' was visualized by plotting a histogram (below). It shows that the distribution is right skewed. In the notebook this skewness will be (partially) removed. As a result, the eventual predictive performance of the machine learning models is improved.

![distribution_target_value](https://user-images.githubusercontent.com/70854452/128375859-3a2a9f1b-d5ad-41da-8573-e6ea13aa6774.png)

Furthermore, a correlation matrix is plotted to look into the relation between numerical + target features. What stands out are the relatively high correlations between the target feature and the features: 'motor_torque(N-m)' (0.51), 'generator_temperature(°C)' (0.39), and 'wind_direction(°)' (0.36). 

In addition, 'motor_torque(N-m)' and 'generator_temperature(°C)' are strongly correlated (0.93).

![correlation_matrix](https://user-images.githubusercontent.com/70854452/128377632-ae43853d-afc2-4e49-a498-6794a2efbd52.png)

The data was also checked for missing data. The bar plot below shows that for several features, but especially for 'blade_length(m)', 'atmospheric_temperature(°C)', 'atmospheric_pressure(Pascal)', and 'windmill_body_temperature(°C)' there is quite some data missing.

![missing_data](https://user-images.githubusercontent.com/70854452/128378686-e614451d-95ed-4194-affb-a9cc64e357a3.png)

Subsequently, we look for potential outliers in the numerical features. These are identified by calculating the z-score. This represents how many standard deviations a value deviates from the mean. The farther away, the more likely the value is an outlier.

In the scatter plots below, a value with a z-score of 3 or more is colored red.

![potential_outliers](https://user-images.githubusercontent.com/70854452/128378974-e276ecfb-fcf1-43b1-94cf-0408fae542f6.png)

## 2. Data Preparation

