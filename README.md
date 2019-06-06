

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

Cardiovascular diseases are the leading cause of death globally. As such, the myriad and complex factors that predicate it are great potential problems for data scientists to tackle.

However, this problem is like many faced by data scientists, and they have no simple solution. The complexity of the problem itself is based on the myriad interactions that occur within the human body. Medical doctors and researchers are still attempting to understand these.

This dataset in my study covers 303 individuals, 14 attributes, and an indicator of the whether they had heart disease.

My approach will include Exploratory Data Analysis, Feature Engineering (minimal required in this example), Testing Multiple Models, including several with GridSearch, and one-by-one analysis the models' top features as they relate current medical knowledge.

As this is a binary classification problem, I will use accuracy score and f_score.  I will just view f_score, since this is interesting and relevant in practice when looking at the potential for a disease.  I will set beta at .8, weighting recall more heavily than precision with the idea that this could be used as an indicator to take preventative action. Accuracy score, however, will be the more relevant measure, since I am looking primarily for which features are most important in predicting the incidence of heart disease and false positives and false negatives should have equal weight in this comparison.

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


There are only 303 records in the dataset, so I kept a close eye on the reliability and significance of the model's results.  This included testing for statistical significance (whether the Pearson correlation was greater than or less than zero) as well as researching current medical knowledge of these features and their association or connection with the presence of heart disease.

After Exploratory Data Analysis, I realized the only feature engineering required would be creating dummy variable, or one-hot encoding, a few features: cp, restecg, slope, and thal.

I ran 14 different models, four of which had a variety of parameters to test through a Cross-Validated Grid Search.

Of the top models, I chose to look more deeply into three classifiers: Bagging, RandomForest, and AdaBoost.  These models provided top scores on the test data as well as readily accessible feature importances.

Most of the model's top features made sense when followed up with research into the common factors related to heart disease according to current medical knowledge.  There were, however, a few features that didn't make sense.  This led me to the Pearson Correlation significance tests and reflection on the downsides of a dataset with only 303 records.

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

There were several takeaways from this project.  This was a great reminder that we should be questioning and skeptical data scientists, and not blindly trust our model's results.  We should particularly not extrapolate meaning where we do not understand any logical rationale for the results.

We can do this by researching the findings of others, testing significance, a variety of models, and not assuming our dataset is without any kind of bias.
