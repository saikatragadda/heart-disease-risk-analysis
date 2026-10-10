# Heart Disease Risk Analysis

Exploratory analysis and classification models for heart disease risk, using CDC 2020 health survey data.

This was a three-person group project for ALY6040 (Data Mining) in the M.S. Data Analytics program at Northeastern University. This repo is a fork of the original team repo: https://github.com/XiaoYangxxxx/ALY6080Group4

## Data

- `heart_2020.csv`: the Kaggle "Personal Key Indicators of Heart Disease" dataset, built from the CDC's 2020 BRFSS survey [add dataset link]
- 319,795 respondents and 18 columns: the target (`HeartDisease`) plus health, lifestyle, and demographic features such as BMI, smoking, sleep time, age group, and general health
- About 9% of respondents report heart disease, so the classes are heavily imbalanced

## What we did

**Cleaning**
- Removed duplicate rows, leaving 301,717 records. There were no missing values.
- Tested BMI and sleep time for normality (Shapiro-Wilk, Q-Q plots) and applied a Box-Cox transformation.
- Encoded categorical variables as numbers: ordered mappings for age group and general health, and 0/1 for yes/no fields.

**Analysis and models**
- Correlation matrix, and BMI and sleep time compared by heart disease status
- Heart disease prevalence by race
- Logistic regression and gradient boosting classifiers to predict heart disease

## Results

| Model | Accuracy | Precision (heart disease) | Recall (heart disease) |
|---|---|---|---|
| Logistic regression | 0.91 | 0.53 | 0.11 |
| Gradient boosting | 0.91 | 0.56 | 0.09 |

The 91% accuracy is close to what you'd get by predicting "no heart disease" for everyone, since about 91% of the data is negative. Recall for the positive class is only around 0.10, so the models miss most actual heart disease cases.

## Known issues in this version

- Class imbalance isn't handled, and the models are evaluated mainly on accuracy.
- The Box-Cox step adds a new `Sleep Time` column but keeps the original `SleepTime`, so sleep is included twice.
- Race and diabetes status are encoded as ordered numbers, even though the categories have no natural order.
- Logistic regression coefficients are compared without scaling the features first.

## Next steps

I shall work on an improved version of the model that addresses these issues: handling class imbalance, one-hot encoding categorical features, removing the duplicate column, and evaluating with recall, precision-recall, and ROC-AUC.

## Files

```
ALY6040 - Group 4 - EDA and Models Code.ipynb   combined team notebook (cleaning, EDA, models)
EDA_xiao.ipynb                                   data cleaning notebook
EDA copy.ipynb                                   earlier EDA draft
rq2.ipynb                                        research question 2 analysis
heart_2020.csv                                   raw data
heart_pure.csv, df_cleaned.csv                   intermediate and cleaned data
```

## Tools

Python, pandas, NumPy, SciPy, scikit-learn, seaborn, matplotlib
