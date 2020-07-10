# Home Credit Default Prediction
![](https://assets.entrepreneur.com/content/3x2/2000/20200406144106-GettyImages-1023100020.jpeg?width=700&crop=2:1)

From the description of the [Kaggle completition](https://www.kaggle.com/c/home-credit-default-risk/overview):

> "Many people struggle to get loans due to insufficient or non-existent credit histories. And, unfortunately, this population is often taken advantage of by untrustworthy lenders.
> Home Credit strives to broaden financial inclusion for the unbanked population by providing a positive and safe borrowing experience. In order to make sure this underserved population has a positive loan experience, Home Credit makes use of a variety of alternative data--including telco and transactional information--to predict their clients' repayment abilities.
> While Home Credit is currently using various statistical and machine learning methods to make these predictions, they're challenging Kagglers to help them unlock the full potential of their data. Doing so will ensure that clients capable of repayment are not rejected and that loans are given with a principal, maturity, and repayment calendar that will empower their clients to be successful."

The goal of this project is to complete a full data science lifecycle including the following topics:

1. __Business Understanding__: Following the Kaggle evaluation the ROCAUC between the predicted probability and the observed target is used.
2. __Data Mining__: The Kaggle competition consists of eight data sets of which only one is used here (application_{train|test}.csv). This is the main table, broken into two files for Train (with TARGET) and Test (without TARGET). Static data for all applications. One row represents one loan in our data sample.No further data mining will be carried out here.
3. __Data Cleaning__: Around 24 % of all the data points are missing, hence a main task is to decide how to approach this problem. Some date type features have negative days as unit which is transformed to number of years (division by -365). Outliers and 'XNA' values are replaced with NaN values. Imputed will be done as follows: NaN's in categorical features will be replaced with 'missing', NaN's in numerical features will be replaced with the median value of the respective feature's value of the TRAIN data set. For XGBoost only categorical imputation will be carried out.
4. __Data Exploration__: There are 121 features plus the target: Target variable: (1 - client with payment difficulties: he/she had late payment more than X days on at least one of the first Y installments of the loan in our sample, 0 - all other cases). Using XGBoost's feature importance the data set will be reduced to the x "best" features. Using basic correlations between features and their missing count helps to recuce the number of useful features even further.
5. __Feature Engineering__: Instead of 'name_education_type' use 'has_higher_education' which includes clients with 'higher education' and 'academic degree'. Combining existing features e.g. amt_annuity / X.amt_credit and amt_credit / amt_income_total might prove useful. Additionally the number of NaN features of a client might be a promising indicator, too. 
6. __Predictive Modeling__: The following models will be applied: A cost-sensitive Logistic regression accounting for the imbalancedness of the target label, a random forest with SMOTE over/undersampling approach using imblearn and finally an XGBoost approach.
7. __Data Visualization__
A collection of the visualizations used will be provided here.

## Future Work
There is a lot left to be done, e.g.
- [ ] apply an exhaustive number of models to the problem
- [ ] many variations of models still need to be tested, especially method that improve imbalanced class handling
- [ ] more and better feature engineering
- [ ] implementation of useful data pipelines
- [ ] improve the parameter tuning process (especially higher automatization)
