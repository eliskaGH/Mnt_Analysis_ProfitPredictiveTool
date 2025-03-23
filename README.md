# Loan Portfolio Analysis: Mnt_Analysis_ProfitPredictiveTool
Analysis of .csv data sets, profit analysis and profit predictive tool (XGBoost classification (XGBClassifier) for default prediction, XGBoost for Profit prediction (based on predicted default))

## 1. Dataset Description
### 1.1 Correlation: IQ vs. Age vs. Distribution Channel
Higher IQ or Age tends to select:
● www (200 CZK),
● Facebook (300 CZK),
● Broker (1000 CZK),
accordingly.
### 1.2 IQ vs. Age
● Higher IQ is associated with higher age
and vice versa.
### 1.3 Default Rate vs. Income
● Overall Default Rate: 0.053
● Default Rate by Income Group (Inc_Gr):
 The default rate decreases as income
increases.
 Lower income levels correlate with a higher
default rate
### 1.4 Metrics:
● N. of observations: 10,000
● N. of defaults: 530
● Default Rate: 0.053
● avg LDG: 0.659
● avg IQ: 132
● avg Age: 42
The most frequent characteristics for:
● Housing: 1 - with parents,
● Educ: 3 - university,
● Inc_Gr: 3 - receives salary between 15 000 CZK and 30 000 CZK

## 2. Profitability analysis
### 2.1 Total Profit of the Loan Portfolio:
Historical total profit of the loan portfolio: -1,776,468.8 CZK
● Profit by Distribution Channel: FB was the most profitable
● Why FB: it is easy to reach
### 2.2 The most and least profitable customers by Channel:
E.g.: The most profitable customers in the Broker Channel:
● Female, single, renting, university degree, salary 15,000 - 30,000 CZK, two
children, average IQ 155.
● Why Facebook is more profitable:
● Lower default rate compared to other channels.

## 3. Historical data
### 3.1 Data preparation:
#### 3.1.1 Assessment of correlations among variables, correlation matrix
#### 3.1.2 Use of one-hot encoded variables
### 3.2 Predictive tool:
#### 3.2.1 Default probability prediction: XGBoost for classification (XGBClassifier)
● set scale_pos_weight to balance rare defaults
● use of SMOTE to create synthetic default cases in the training set
● Accuracy: 0.9385, AUC-ROC: 0.8488, F1-score: 0.3881
● Note: LogisticRegression() or DecisionTreeRegressor were weaker
● Note: the model is rather weak in default detection (imbalanced variable)
#### 3.2.2 Profit prediction using default probability from 1/: XGBoost Regressor
● Model Performance: MAE: 1495.03, RMSE: 4033.73, R²: 0.1732
● Note: 1-step models of profit (linear regression, polynomial regression,
XGBRegressor) were weaker

## 4. Broker’s list
### 4.1 The predictive tool for the Broker’s list profit prediction:
● default_prob and profit_predict were evaluated
● The top 50 clients with the highest profitability were evaluated found:
● [280, 294, 156, 243, 225, 209, 231, 287, 295, 304, 3725, 2896, 2786, 3506, 227,
293, 1973, 1949, 290, 3440, 3475, 1204, 3728, 3658, 2908, 2943, 611, 1939,
1978, 1917, 2075, 3650, 229, 1970, 2080, 622, 237, 1230, 1911, 687, 633, 1228,
589, 1173, 3723, 2855, 2042, 3581, 1984, 2934]
● Most of the top clients had own housing and 1-Inc_Gr:
4.2 Progress or not with this product
urrent situation
### 4.2 Progress or not with this product
● The current product is not profitable (based on historical data)
● The proposed model is weak in default prediction and leads to the bias in the total
profit
Recommendations
● Progress with this product only for profitable clients
● Additional analysis of default prediction
● Separate model for Broker channel, defaulters, etc.
