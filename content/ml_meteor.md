---
layout: default
---

## Machine Learning Analysis: Classifying Meteor Type ##

_Executive Summary_

__Overview__

Unbalanced datasets with limited features present a distinct challenge for Machine Learning algorithms. This project used the meteorite landings dataset from Nasa (https://data.nasa.gov/Space-Science/Meteorite-Landings/gh4g-9sfh) and machine learning to identify the four overall meteorite types using only the meterites falling method, weight and geospatial information. The data set contained information about documented meteorite landings from the years 860 to 2013.

__Problem Summary__

Use machine learning to classify target variable ('types') in unbalanced dataset with limited features.

__Solution Summary__

Preprocessing was an important step in the solution process. NA's represented approximately 6% of the original dataset and were removed.The target variable meteor classification was simplified from 422 types to four main types - chondrites, achondrites, iron meteorites, stony iron meteorites. Fall was transformed into a dummy variable. The data was split into a 60/40 stratified test/train set. The stratification was used to handle the imbalanced class issues.  

* KNN with standard parameters & KNN with GridSearchCV- Supervised machine learning algorithm that determines the K nearest neighbors of an instance to classify that instance. GridSearchCV uses a parameter grid to iteratively test and determine the parameter values which   yeild the highest accuracy (default). 

* Adaboost & Adaboost with GridSearchCV- Ensemble learning method that combines the predictions of multiple weaker learners using weights, aiming to create a stronger overall predictor. GridSearchCV functions as above. 

* Random Forest & Random Forest with GridSearchCV - Ensemble learning method which constructs multiple decision trees. Each tree is trained on a subset of randomly selected features and the final classification is determined by a majority vote. GridSearchCV functions as above.

__Conclusions & Future Work__ 

While all classifiers performed well at identifying Chondrites (the most prevalent class) and Iron (the second most prevalant class) with >90% accuracy, Random Forest with GridSearch CV had the best overall performance for the less prevelant classes. Random Forest with GridSearchCV had an training accuracy of 86% and a testing accuracy of 83% (3% difference). This classifier had an F1 sore of 0.83. Despite the limited features and unbalanced data, machine learning was sucessfull in identifying the four major types of meteorite classifications. With additional features, models could reasonabley identify meteorite subtypes. 

[View Sample Code in Google Colab](https://colab.research.google.com/drive/1DkQqs70l1cFm5f36WzJPPHQCLRoloL40?usp=sharing)

[All Projects](/index.html)
