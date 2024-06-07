# multivariable-non-linear-regression-car-price-prediction
This project the continous multivariable linear regression car price prediction. 
For non-linear regression model, I mainly use KNN, Decision Tree, SVR, GBM and XGBoosting. My best MSE here is 0.135 by XGBoosting. So for car price dataset, its better to use linear regression model for prediction. 

## Basic steps
I first tried to implement by different non-parametric methods. Then for each methods I run parameter adjustment. For the best parameters, I use cross validation to get the average accuracy then check if its overfitting or underfitting. 

## Data cleaning
Data cleaning step is as same as previous one. I separate CarName to "Company" and "Model" columns. Then clean up some typos. At last, I normalized numeric features and convert category features into numeric variables. 

## Pre-checking
Pre-checking process is as same as multivariable linear regression. I checked normally, linearity, independence and homoscedasticity.
For outlier part, I checked residual, high leverage points and cook's distance. 

## KNN method
KNN method is kind of naive or lazy regression method. It is sensitive to data size. If data size is increased, this method becomes too much slower. For points at the beginning or at the last, it not accurate at all. On plot, it almost happens as a horizontal line. So I just implement this as a practice. 
My best result: 
K = 1, mse = 0.218563, r2 = 0.562518

## Decision Tree/Random Forest
If Decision Tree and Random Forest model happens at the same time, I prefre using Random Forest because this algorithm is creating N Decision Trees. Among them, this algorithm will pick the best tree as final model. 
After parameter tuning: 
n_estimators = 300, max_depth = 12, min_sample_split = 2, min_sample_leaf = 1, mse = 0.039987, r2 = 0.103695.

From this result, at first I think it will be my best model. Then I check if its overfitting or underfitted. 
|dataset to train|mse|R2|
|----------------|---|--|
|training|0.01253|0.977759|
|testing|0.039986|0.91996|
This model is perfect!

But, when I run cross validation, it shows me:
Average MSE: 0.1947
Average R2: 0.2290

The result here is totally different with my previous result. So my model is overfitting which means the tree I use is too much complex. So I need pruning further. 




