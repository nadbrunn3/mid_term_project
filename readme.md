# Credit Card Approval Prediction

## Data Source

The data used in this project is from kaggle and can be found here: [https://www.kaggle.com/datasets/rikdifos/credit-card-approval-prediction?datasetId=426827&sortBy=voteCount](https://www.kaggle.com/datasets/rikdifos/credit-card-approval-prediction?datasetId=426827&sortBy=voteCount)

## Context

Credit score cards are a common risk control method in the financial industry. It uses personal information and data submitted by credit card applicants to predict the probability of future defaults and credit card borrowings. The bank is able to decide whether to issue a credit card to the applicant. Credit scores can objectively quantify the magnitude of risk.

At present, with the development of machine learning algorithms. More predictive methods such as Boosting, Random Forest, and Support Vector Machines have been introduced into credit card scoring. However, these methods often do not have good transparency. It may be difficult to provide customers and regulators with a reason for rejection or acceptance.

## Task

Build a machine learning model to predict if an applicant is 'good' or 'bad' client.  

- Exploratory Data Analysis
- Target Feature Engineering
- Build a machine learning model to predict if an applicant is 'good' or 'bad' client. This will help to approve or decline future applicants based on the given criteria.

## ⚠️ Main Issues

- The target feature is not given. We first need to classify the loan status and compute a target feature.
- The data is highly imbalanced which is a big problem in this project

## **Data Cleaning**

1. There are several Null Values in Occupation Feature which got the lable 'Others'
2. Income Feature is treated as categorical with bins ['<=100k', '100k-200k', '200k-300k', '300k-400k', '400k+' ]
3. Underrepresented classes are grouped together.
4. Days_birth, and days_employed are given in negative days counting backward.
5. Outliers present in cnt_children, cnt_family_member, days_employed

## 🥉 **Target Feature**

1) # Grouping the classes together in GOOD, NEUTRAL and BAD:

`rename = {'X': 'Good', 'C': 'Good', '0': 'Good', '1': 'Neutral', '2': 'Bad', '3': 'Bad', '5': 'Bad'}`

- more NEUTRAL than GOOD records will be classified as 1: 'not approved'
- one BAD status will be automatically classified as 1: 'not approved'
- Customers which have more GOOD than NEUTRAL will be calssified as 0: 'approved'

## ⛔ **Multicollinearity**

- High corrletion between 'cnt_children' and 'cnt_family_member'
- Because of the correlation the model will onyl consider 'cnt_children'

## D**ata Processing**

1. Train Test Split
2. One Hot Encoding of categorical values
3. PowerTransforming and Scaling numeric values

## **Model Testing**

1. Logistic Regression
2. KNeighbors (n = 2,3,4)
3. Decistion Tree Classifier

## 📝 **Result**

We want to improve the model towards more positiv 'Not Approved' Classification and an increase in ROC AUC Score.

The DTC has the best prediction score for the tested parameters.

## 🏃‍♀️ **Further Steps needed**

Further increasing the prediction value for the 'Not Approved' (1) also by considering having more false negatives.

Since the target is highly imbalanced next steps are:

1) Weighted Target

2) GridSeach

3) Testing other Classification Models (RandomForste ie.)
