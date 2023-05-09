# Credit Risk Classification
Credit Risk Classification


## Overview of the Analysis


### * Purpose of the analysis

Data was used to determine whether a loan will be healthy or it will be high-risk based on information from users.

### * Financial information data used

Values that included in the below list were used for the analysis:

- loan_size 
- interest_rate
- borrower_income
- debt_to_income
- num_of_accounts
- derogatory_marks
- total_debt
- loan_status

A value of 0 in the “loan_status” column means that the loan is healthy. A value of 1 means that the loan has a high risk of defaulting. This is the variable that was used to predict. All the rest of the variables were used as input.

Data includes 75036 samples of healthy status and 2500 of high-risk.

### * Basic information about the variables 

All variables are numerical. Input variables are:

- loan_size 
- interest_rate
- borrower_income
- debt_to_income
- num_of_accounts
- derogatory_marks
- total_debt

Output variable is loan_status which can take a value of either 1 or 0 as explained above.

### * Process stages for the machine learning algorithms 

The data was loaded from a CSV file and then split between features which consisted of all the input variables (X) and the the loan_status (y) which is the variable to predict. The dataset was further split into train and test set using sklearn's train_test_split function.


### * Methods used

2 models that used `LogisticRegression`from sklearn were used for the analysis. The first model used the original dataset split into training and testing datasets.

In the second model a `LogisticRegression` was also used, but the training dataset was enlarged with a RandomOverSampler module from imbalanced-learn. This attempted to address the imbalance between Healthy and High-Risk samples as described above (75036 healthy status samples vs 2500 high-risk).

## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

### Machine Learning Model 1:

`LogisticRegression` with originally split dataset

#### General scores Learning model 1:

Training Data Score: 0.9921240885954051
Testing Data Score: 0.9918489475856377
Accuracy Score: 0.9918489475856377

#### Confusion matrix model 1:

array([[18663,   102],
       [   56,   563]], dtype=int64)


#### Metrics Learning model 1:

                precision    recall  f1-score   support

  Healthy Loan       1.00      0.99      1.00     18765
High-Risk Loan       0.85      0.91      0.88       619

      accuracy                           0.99     19384
     macro avg       0.92      0.95      0.94     19384
  weighted avg       0.99      0.99      0.99     19384

The model correctly classified Healthy loans as Healthy all the times. A Healthy loan was incorrectly classified as High Risk only 1% of the time. High-Risk loans were incorrectly classified as Healthy 15% of the times. High Risk Loans were correctly classified as High-Risk 91% of the times. 

The total model accuracy 99.18%. 


### Machine Learning Model 2:

`LogisticRegression` with added samples using the `RandomOverSampler` module from the imbalanced-learn library to resample the data. The healthy and high-risk loans have an equal number of data points. 

#### General scores Learning model 2:

Training Data Score: 0.9947308560359688
Testing Data Score: 0.9938093272802311
Accuracy Score: 0.9938093272802311

#### Confusion matrix model 2:

array([[18649,   116],
       [    4,   615]], dtype=int64)

#### Metrics Learning model 2:

                precision    recall  f1-score   support

  Healthy Loan       1.00      0.99      1.00     18765
High-Risk Loan       0.84      0.99      0.91       619

      accuracy                           0.99     19384
     macro avg       0.92      0.99      0.95     19384
  weighted avg       0.99      0.99      0.99     19384

The model correctly classified Healthy loans as Healthy all the times. A Healthy loan was incorrectly classified as High Risk only 1% of the time. High-Risk loans were incorrectly classified as Healthy 16% of the times. High Risk Loans were correctly classified as High-Risk 99% of the times. 

The total model accuracy 99.38%. 

Adjusting the imbalance improved the model's capability to correctly label the high risk loans

## Summary

Summarise the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Which one seems to perform best? How do you know it performs best?
* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

If you do not recommend any of the models, please justify your reasoning.
