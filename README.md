

## Objectives:
I will attempt to find the main contributors to heart disease through the UCI Heart Disease dataset.

#### Please see my blog on this project here: https://medium.com/@HawkeyeRye/using-data-science-to-predict-heart-disease-69228f78dc0

The following was used in my analysis:

**Data:**
- https://github.com/1RyanGoodman/HeartDiseasePrediction/blob/master/heart.csv
- or https://www.kaggle.com/ronitf/heart-disease-uci

**Python Packages:**
- numpy
- pandas
- os
- matplotlib
- time
- sklearn
- seaborn

### Introduction

Cardiovascular diseases are the leading cause of death globally. As such, the myriad and complex factors that predicate it are great potential problems for data scientists to tackle.

However, this problem is like many faced by data scientists, and they have no simple solution. The complexity of the problem itself is based on the myriad interactions that occur within the human body. Medical doctors and researchers are still attempting to understand these.

### The Data and the Problem

This dataset in my study covers 303 individuals, 14 attributes, and an indicator of the whether they had heart disease.

My approach will include Exploratory Data Analysis, Feature Engineering (minimal required in this example), Testing Multiple Models, including several with GridSearch, and one-by-one analysis the models' top features as they relate current medical knowledge.

As this is a binary classification problem, I will use accuracy score and f_score.  I will just view f_score, since this is interesting and relevant in practice when looking at the potential for a disease.  I will set beta at .8, weighting recall more heavily than precision with the idea that this could be used as an indicator to take preventative action. Accuracy score, however, will be the more relevant measure, since I am looking primarily for which features are most important in predicting the incidence of heart disease and false positives and false negatives should have equal weight in this comparison.

#### The Features

Exploratory Data Analysis
age: The person's age in years
sex: The person's sex (1 = male, 0 = female)
cp: The chest pain experienced (Value 1: typical angina, Value 2: atypical angina, Value 3: non-anginal pain, Value 4: asymptomatic)
trestbps: The person's resting blood pressure (mm Hg on admission to the hospital)
chol: The person's cholesterol measurement in mg/dl
fbs: The person's fasting blood sugar (> 120 mg/dl, 1 = true; 0 = false)
restecg: Resting electrocardiographic measurement (0 = normal, 1 = having ST-T wave abnormality, 2 = showing probable or definite left ventricular hypertrophy by Estes' criteria)
thalach: The person's maximum heart rate achieved
exang: Exercise induced angina (1 = yes; 0 = no)
oldpeak: ST depression induced by exercise relative to rest ('ST' relates to positions on the ECG plot)
slope: the slope of the peak exercise ST segment (Value 1: upsloping, Value 2: flat, Value 3: downsloping)
ca: The number of major vessels (0-3)
thal: A blood disorder called thalassemia (3 = normal; 6 = fixed defect; 7 = reversable defect)
target: Heart disease (0 = no, 1 = yes)

### The Analysis

There are only 303 records in the dataset, so I kept a close eye on the reliability and significance of the model's results.  This included testing for statistical significance (whether the Pearson correlation was greater than or less than zero) as well as researching current medical knowledge of these features and their association or connection with the presence of heart disease.

After Exploratory Data Analysis, I realized the only feature engineering required would be creating dummy variable, or one-hot encoding, a few features: cp, restecg, slope, and thal.

#### I will use accuracy score and f_score as my metrics for this binary classification problem.
I will look at **f_score**, since this is interesting and relevant in practice when looking at the potential for a disease.  I will set beta at .8, weighting recall more heavily than precision with the idea that this could be used as an indicator to take preventative action.  While only theoretical, this higher recall sensitivity would potentially be used to encourage change in behavior like diet and exercise.  One would possibly argue that this sensitivity would be too high if the outcome were related to actual prescription of medications related to heart disease.<br>

**Accuracy score** will be the most relevant measure for my purposes, since I am looking primarily for which features are most important in predicting the incidence of heart disease.  So, accuracy score will weight false positives and false negatives equally.

I ran 14 different models, four of which had a variety of parameters to test through a Cross-Validated Grid Search.

My Final model is a VotingClassifier based on the top-scoring models.  I chose the top three models, but I only used one of the Naive Bayes models (I picked BernoulliNB), because the logic they use to train will be very similar.  So, I wouldn't expect any added value from an ensemble such similar models.

Of the top models, I chose to look more deeply into three classifiers: Bagging, RandomForest, and AdaBoost.  These models provided top scores on the test data as well as readily accessible feature importances.

Most of the model's top features made sense when followed up with research into the common factors related to heart disease according to current medical knowledge.  There were, however, a few features that didn't make sense.  This led me to the Pearson Correlation significance tests and reflection on the downsides of a dataset with only 303 records.

Finally, I looked at the feature importances of the VotingClassifier.

It was nice to see the top six features of the VotingClassifier are among those that I've already researched.  This is encouraging and makes sense since the VotingClassifier is an amalgam of the top models.

### Results:
The main factors predictive of the incidence of heart disease included:
**oldpeak** - the ST Depression in an ECG (Electrocardiogram).
**ca** - is the number of major vessels (0–3) colored by flouroscopy.
**cp_0** - (typical angina)
**thalach** - the maximum heart rate achieved
**thal_2** - thalassemia - reversible defect

I corroborated these features with sources online in my research.

The few questionable features included:
**age** - Age, as a negative correlation
**chol** - Total Cholesterol, as a negative correlation
**trestbps - Resting Blood Pressure, as a negative correlation

I have dismissed the model results for these features primarily due to being contrary to medical knowledge, but also either statistically insignificant (trestbps, chol) or having been introduced through an unknown bias in the study (age).

### Summary:

We should be skeptical data scientists, and not blindly trust our models' results. We should be particularly careful when tempted to extrapolate meaning where we do not understand any logical rationale for the results. We can do this by researching the findings of others, testing significance, testing a variety of models, and not assuming our dataset is free of any bias.
We like to solve problems, but the problems we try to solve are often much more complex than applying your typical machine learning model and simply reading out results that revolutionize the world. We need to ask a lot of questions about each specific case.

- Does machine learning work for this case? Or, should I just stick with descriptive statistics?
- How many different models should I test?
- What is the specialized level of knowledge required to understand the results?
- Do the results corroborate the established understanding in this field and can we defend the results if they do not?

For my particular study, I have a few answers to these scrutinizing questions.
Machine learning should work for this case, but a much larger dataset would be required. I would also need to have an in-depth understanding of how the dataset was created to make sure I understand any potential biases. Finally, this is a study where an engaged partnership with trained medical professionals would be essential.
