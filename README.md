# KKBOX
KKBOX project on Kaggle

For details about the competition visit: https://www.kaggle.com/c/kkbox-churn-prediction-challenge/data

# Project Overview

**Objective:** The main idea of the project is to predict churn for KKBOX customers.

**Data:**
*  Transactions: Dataset with aprox 21.5 million records and features related with transactions of each customer: transaction date, end date, payment method, etc. Amount of unique records: 2.3 million records
*  Users: 6.7 million unique records with information about the customer (age, city, gender, etc)
*  Logs: 30 million records with customer behavior per day (# of unique songs played, total seconds played, etc). Amount of unique records: 1.8 million records
*  Train: Aprox 1 million records indicating if customer has churn or renewal.

## Code and Resources used:

**Python Version**: 3.7

**Packages**: pandas, numpy, sklearn, matplotlib, seaborn.

**Fixing Oversampling:** https://www.youtube.com/watch?v=OJedgzdipC0

For every dataset I followed this strategy:

## **1.  Exploratoy Data Analysis (EDA)**

*  Loading data
*  Statistics of the data frame
*  Data visualization
*  Data Cleaning
*  Fixing formats
## **2.  Feature Engineering**

There are 2 challenging datasets (logs and transactions) because  they have duplicated records due to their nature.

For logs dataset I followed these steps:

*  Create features based on the average of the original feature.
*  Data transformations: Most of the features were skewed to the right. I used the log transformation.
*  Outlier detection

For transactions I followed these steps:
*  Create features: Group the original dataset and for each customer create:
    * Amount of transactions.
    * Most frequent plan.
    * Most frequent payment method.
    * Revenue (sum of the amount paid for each transaction)
    * Auto renewal (most frequent decision)
    * Amount of cancelations (sum of cancelations for every user)
    * Most frequent quarter of transaction (the most frequent quarter of the year when the customer makes transactions)
*  Outlier detection

After dealing with all datasets separately, I merged all datasets in one and then I applied the strategy of Exploratory Data Analysis and Feature Engineering again.

Customers with 0 and 2 years of tenure are more likely to have churn.

<img src= "https://github.com/jsroa15/KKBOX/blob/main/tenure.png?raw=true" width="500"/>

<img src= "https://github.com/jsroa15/KKBOX/blob/main/eda.png?raw=true" width="600"/>


## **3.  Modeling and Evaluation**

The data has a problem bacause it's unbalanced. Almost 94% of data has no churn Vs 6% with churn.To solve this I used oversampling to balance data. The resource of how to use oversampling is the Resources section of this Repo.

### Baseline Model:
**Naive Bayes Classifier**
| ROC AUC Score | Accuracy | F1 Score | Precision | Recall |
|---------------|----------|----------|-----------|--------|
| 79.68         | 79.04    | 28.95    | 18.54     | 66     |



