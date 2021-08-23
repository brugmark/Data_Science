# Churn Risk Rate Prediction (HackerEarth)
This notebook is created as part of a [HackerEarth competition](https://www.hackerearth.com/challenges/competitive/hackerearth-machine-learning-challenge-predict-customer-churn/). The goal is to predict the churn score for a website based on multiple features related to a user’s demographic, browsing behavior, and historical purchase data, among other details.

For this purpose, the data is explored and prepared and several algorithms (Random Forest, Kernel SVM, Neural Network) are optimized using GridSearchCV. This has resulted in a final score of 74.9 (100 * f1-score).

## 1. Data Understanding
The distribution of the target feature 'churn_risk_score' is determined by plotting a histogram (below). It shows that the distribution is left skewed. In the notebook this skewness is removed. As a result, the eventual predictive performance of the machine learning models improved.

![distribution_target_value](https://user-images.githubusercontent.com/70854452/129757585-00f7198b-4dd0-4020-a291-ec5ee3f604cd.PNG)

Furthermore, a correlation matrix is plotted to look into the relation between numerical + target features.

![correlation_matrix](https://user-images.githubusercontent.com/70854452/129757703-73d29a44-a298-4d9b-8db7-ec6143b8f90b.PNG)

The relation between the categorical + target features is assessed using box and bar plots. To exemplify this, a plot for one of the categorical values ('region_category') is shown below.

![relation_categorical_and_target_variabels](https://user-images.githubusercontent.com/70854452/129757936-371f144d-aa2c-4976-afcd-4f1c0faae23b.png)

Next the data is checked for missing values. The plots to assess the relation between the categorical + target features already revealed some non-'NA' missing values for the following features:
- gender: 'unknown'
- joined_through_referral: '?'
- medium_of_operation: '?'
- avg_frequency_login_days: 'Error'

![missing_data](https://user-images.githubusercontent.com/70854452/129758814-0108de51-d985-4070-a594-29a25b2d9a73.png)

Subsequently, potential outliers in the numerical features are flagged. To exemplify this, the scatter plot below is shown. In this plot a value with a z-score of 3 or more is colored red.

![potential_outliers](https://user-images.githubusercontent.com/70854452/129759035-c65ac7a3-13b9-4c49-8497-442c0742e735.png)

## 2. Data Preparation
Next, the following steps are taken to prepare the data:
- Reformat
- Remove outliers
- Encoding
- Fill missing data
- Split
- Standardization

## 3. Modeling
Each algorithm is optimized/evaluated using:
- Hyper parameter optimization 
- K-fold cross validation (f1_macro)

In addition, learning curves are created to determine whether over- or underfitting occurred.

![learning_curves](https://user-images.githubusercontent.com/70854452/129759419-903564b2-9c99-478c-9e0d-6807cd3de8bf.png)

In the end, it turned out that the Random Forest algorithm resulted in the best prediction.