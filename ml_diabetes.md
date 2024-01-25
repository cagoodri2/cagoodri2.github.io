---
layout: default
---

## Gaussian Naive Bayes to Predict Diabetes Outcome ###

_Executive Summary_

__Overview__

As reported by the World Health Organization (WHO), diabetes has become a global epidemic, with approximately 422 million adults living with the condition in 2014. It is predicted to be the seventh leading cause of death by 2030 (1).  Gaussian Naive Bayes was applied to diagnostic measurements to predict a diabetes diagnosis. The dataset was sourced from the National Institute of Diabetes and Digestive and Kidney Diseases and accessed via Kaggle.com. It contained 768 observations from females at least 21 years old of Pima Indian heritage. Predictor variables included pregnancies, glucose, blood pressure, skin thickness, insulin, BMI, diabetes pedigree function, and age. The target variable was outcome.

__Problem Summary__

Gaussian Naive Bayes was applied to diagnostic measurements to predict a diabetes diagnosis.

__Solution Summary__

Gaussian Naive Bayes: Gaussian Naïve Bayes was applied using 10-fold cross validation with tuning of variable smoothing. Three versions of the dataset were utilized to improve model accuracy: base dataset, normalized dataset, and a reduced features dataset with highly correlated features removed. The best performing Gaussian Naïve Bayes was the reduced dataset version with the highest F1 at 0.75 and the highest testing accuracy score at 0.75.  

__Conclusions__

A reduced dataset outperformed the baseline & normalized dataset in diabetes prediction. Alternative models may fit the dataset better improving overall accuracy & F1 scores. 

1) World Health Organization. (2016). Global report on diabetes. Retrieved from https://www.who.int/publications/i/item/9789241565257 



[Sample of Technical Report](./diabetes_tech.html)

[Sample of Python Code](./diabetes_python.html)

[All Projects](./)
