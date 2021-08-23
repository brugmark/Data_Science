# House Prices - Advanced Regression Techniques (Kaggle)
This notebook is created as part of a [Getting Started Prediction competition on Kaggle](https://www.kaggle.com/c/house-prices-advanced-regression-techniques). The goal is to predict housing prices based on several house characteristics. In addition, another more important general goal is to apply machine learning knowledge in practice and learn from other notebooks and data enthusiasts/scientists.

For this purpose, the data is explored, prepared and several algorithms:
- Linear
- Ridge
- Lasso
- Elastic Net
- Decision Tree
- Random Forest
- Gradient Boosting Tree
- Light Gradient Boosting Machine
- Extreme Gradient Boosting
- Neural Network)

Are optimized using GridSearchCV and RFECV. This has resulted in a top 15% score.

## 1. Data Understanding
The distribution of the target feature 'SalePrice' is determined by plotting a histogram (below). It shows that the distribution is right skewed. In the notebook this skewness is removed. As a result, the eventual predictive performance of the machine learning models improved.

![distribution_target_value](https://user-images.githubusercontent.com/70854452/130472080-822bbcc3-de19-4f91-98dc-0b5ac237c092.PNG)

Furthermore, a correlation matrix is plotted to look into the relation between numerical + target features.

![correlation_matrix](https://user-images.githubusercontent.com/70854452/130472273-94f39a9e-2d8e-4dcb-ab76-d130eac02e5b.PNG)

The relation between the categorical + target features is assessed using bar plots. To exemplify this, a plot for one of the categorical values ('MSZoning') is shown below.

![relation_categorical_and_target_variables](https://user-images.githubusercontent.com/70854452/130472867-9e151059-9e15-46d4-992a-f2431040f09f.png)

Next the data is checked for missing values. The bar plot below shows that, especially for the features 'LotFrontage', 'GarageYrBlt', and 'MasVnrArea', there is quite some data missing.

![missing_data](https://user-images.githubusercontent.com/70854452/130472959-49c3ef06-918f-438f-8782-062bfa129c69.png)

Subsequently, potential outliers in the numerical features are flagged. To exemplify this, the scatter plot below is shown. In this plot a value with a z-score of 3 or more is colored red.

![potential_outliers](https://user-images.githubusercontent.com/70854452/130473350-c77062b9-a745-4f73-924b-768670496453.png)

## 2. Data Preparation
Next, the following steps are taken to prepare the data:
- Select
- Reformat
- Construct (feature engineering)
- Integrate
- Clean

Including normalization of the target feature 'SalePrice':

![distribution_target_value_normalized](https://user-images.githubusercontent.com/70854452/130473572-d08623a7-e755-4c6f-8298-178f3acd7204.png)

## 3. Modeling
Each algorithm is optimized/evaluated using:
- Hyper parameter optimization 
- K-fold cross validation (neg_root_mean_squared_error)

In addition, learning curves are created to determine whether over- or underfitting occurred.

![learning_curves](https://user-images.githubusercontent.com/70854452/130474068-6762357f-f7b5-4703-8cca-7483c6f584fe.png)

And recursive feature elimination is applied:

![recursive_feature_elimination](https://user-images.githubusercontent.com/70854452/130474124-de826a7c-34d1-4354-9e2a-472241b3ade1.png)

In the end, it turned out that the Elastic Net algorithm resulted in the best prediction.
