# HeartDiseasePrediction

https://github.com/1RyanGoodman/HeartDiseasePrediction

One probably doesn't need to be convinced that understanding heart disease is important for global health.  However, one simple statistic should convince the uninformed... Cardiovascular diseases are the leading cause of death globally.
https://en.wikipedia.org/wiki/Cardiovascular_disease#cite_note-GBD2015De-4

While the sample size in the analysis in this model only covers 303 individuals, we are able to clearly see, visually, patterns around certain characteristics that are correlated with heart disease.  In my summary, I highlight three specific characteristics with these correlations.  Some of these will be surprising...

The feature "thalach" refers to the maximum heart rate achieved.  Higher levels of this are shown to be correlated with a higher probability of heart disease.  This seems to implies the heart is attempting to overwork in incidences of heart disease, attempting to overcompensate for functional deficiency.

While the correlation with age is not surprising, it is very surprising that this correlation with heart disease is negative over the age ranges in the study (from around 35 to 75).  I would suspect that heart disease is either more likely affecting those who are younger and living less healthy lives.  Those who survive to old age are then a self-selecting population who were less likely to have had heart disease at a younger age.  Their number would be reduced by those who had heart disease at a younger age and sadly passed away earlier than the average person.  There might also be some factor here where those who are older are visiting doctors more frequently and addressing their heart issues with medication, but I cannot conclude that theory as it was not part of my study.

Finally, cholesterol is surprising negatively correlated with heart disease.
This medical article confirms that a person's serum cholesterol can indicate risk for heart disease. https://www.medicalnewstoday.com/articles/321519.php
The article also describes how serum cholesterol is calculated...
Total serum cholesterol is calculated by adding the HDL level, the LDL level, and 20 percent of the triglyceride level present in a blood sample. Frankly, I do not fully understand the science behind all of this, but I do see an interesting statistical consideration at play here.  While one may conclude that lower serum cholesterol is bad from this study, it's actually quite complicated.
According to the American Heart Association, low-density lipoprotein (LDL) cholesterol is often considered bad, while high-density lipoprotein (HDL) cholesterol is considered good. These are added into the serum cholesterol calculation.  Furthermore, it appears that serum cholesterol is positively correlated with age.  Thus, we have a classic causality problem here. More analysis would have to be done to conclude that the lower serum cholesterol is bad as indicated by the higher incidence of heart disease. It could be that the truly weightier factor is age, which also is negatively correlated with heart disease over the range studied but positively correlated with serum cholesterol.

The complexity of this type of problem is a great example of where analytics and data science can provide such helpful insight into the very important field of health care.
