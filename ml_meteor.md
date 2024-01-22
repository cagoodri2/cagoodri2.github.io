---
layout: default
---

## Predicting Meteor Type with Machine Learning ##

_Executive Summary_

__Overview__

Unbalanced datasets with limited features present a distinct challenge for Machine Learning algorithms. This project used the meteorite landings dataset from Nasa (https://data.nasa.gov/Space-Science/Meteorite-Landings/gh4g-9sfh) and machine learning to identify the four overall meteorite types using only the meterites falling method, weight and geospatial information. The data set contained information about documented meteorite landings from the years 860 to 2013. One year was in error within the csv of the original dataset (2101), but years were used for exploratory purposes only. Information included the meteorites name, id, nametype, classification, mass (g), the year it fell and the location of discovery. The dataset also included whether the meteorite was found while falling or immediately after falling vs. some time after the meteorite fell ('fall'). 

__Problem Summary__

Utilize KNN, KNN with GridSearchCV, Adaboost, Adaboost with GridSearchCV, Random Forest, Random Forest with GridSearch CV to classify target variable ('types') in unbalanced dataset with limited features.

__Solution Summary__

Preprocessing was an important step in the solution process. NA's represented approximately 6% of the original dataset and were removed.The target variable meteor classification was simplified from 422 types to four main types - chondrites, achondrites, iron meteorites, stony iron meteorites.Fall was transformed into a dummy variable. The data was split into a 60/40 stratified test/train set. 

KNN with standard parameters
KNN with GridSearchCV
Adaboost
Adaboost with GridSearchCV
Random Forests
Random Forset with GridSearchCV were used to classify the target variable ('types'). 

__Conclusions & Future Work__ 
While all classifiers performed well at identifying Chondrites (the most prevalent class) and Iron (the second most prevalant class), Random Forest with GridSearch CV had the best overall performance. Random Forest with GridSearchCV had an training accuracy of 86% and a testing accuracy of 83% (3% difference). This classifier had an F1 sore of 0.83. Despite the limited features, machine learning was sucessfull in identifying the four major types of meteorite classifications.


Link to technical report sample
Link to python code

[back](./)
