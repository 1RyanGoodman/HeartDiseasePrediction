# HeartDiseasePrediction

See my blog here: https://medium.com/@HawkeyeRye/using-data-science-to-predict-heart-disease-69228f78dc0

https://github.com/1RyanGoodman/HeartDiseasePrediction

One probably doesn't need to be convinced that understanding heart disease is important for global health.  However, one simple statistic should convince the uninformed... Cardiovascular diseases are the leading cause of death globally.
https://en.wikipedia.org/wiki/Cardiovascular_disease#cite_note-GBD2015De-4

While the sample size in the analysis in this model only covers 303 individuals, we are able to clearly see, visually, patterns around certain characteristics that are correlated with heart disease.  In my summary, I highlight three specific attributes, some of which will be surprising...

https://www.nhs.uk/news/heart-and-lungs/study-says-theres-no-link-between-cholesterol-and-heart-disease/

The feature "thalach" refers to the maximum heart rate achieved.  Higher levels of this are shown to be correlated with a higher probability of heart disease.  This seems to imply the heart is overworking in cases of heart disease, attempting to overcompensate for the deficiencies caused by heart disease.  This positive correlation is intuitive... An unhealthy individual put under a stress test, like 5 minutes of running, for example, will have a higher heart rate than someone who is healthier.

While the correlation with age is not surprising, it is very surprising that this correlation with heart disease is negative over the age ranges in the study (from around 35 to 75).  My inference here is that those who survive to old age are a self-selecting population who were less likely to have had heart disease at a younger age.  Their number would be reduced by those who had heart disease at a younger age and sadly passed away earlier than the average person.  There might also be some factor here where those who are older visit doctors more frequently and thus are more likely to be addressing their heart issues with medication, but I cannot conclude that theory as it was not part of my study.  In general, this is a perplexing statistic.  We do see that age should be positively correlated with heart disease, but this may be due to other factors or the small sample size of the study.


Finally, total cholesterol is surprisingly negatively correlated with heart disease. This medical article confirms that a person's serum cholesterol can indicate risk for heart disease. https://www.medicalnewstoday.com/articles/321519.php
The article also describes how serum cholesterol is calculated...
Total serum cholesterol is calculated by adding the HDL level, the LDL level, and 20 percent of the triglyceride level present in a blood sample. Frankly, I do not fully understand the science behind all of this, but I do see an interesting statistical consideration at play here.  While one may conclude that lower serum cholesterol is bad from this study, it's actually more complicated than that.
According to the American Heart Association, low-density lipoprotein (LDL) cholesterol is often considered bad, while high-density lipoprotein (HDL) cholesterol is considered good. These are added into the serum cholesterol calculation.  Furthermore, it appears that total serum cholesterol is positively correlated with age.  Thus, we have a classic causality problem here. To address this, I adjusted each person's cholesterol based on the coefficients of a linear regression between age and cholesterol.  After removing the effect of age, which was already negatively correlated with the presence of heart disease, the correlation between total cholesterol and the presence of heart disease decreased from -.085 to -.038.  Again, this could also be affected by outside factors or covariance with other features in the study.

The complexity of this type of problem is a great example of where analytics and data science can provide such helpful insight into the very important field of health care.  It also sheds light on the necessity of creating a study with a perspective on the possibilities of covariance as well the the necessity of a large enough sample size to draw significant conclusions.
