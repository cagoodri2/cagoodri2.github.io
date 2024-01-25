---
layout: default
---

## Time Series Analysis: Severity Measures in Cardiac Related Hospital Admissions ###

_Executive Summary_

__Overview__

Medical time series present a unique opportunity for time series analysis. Exploring admissions data can
provide insight into the demands placed on healthcare teams, hospital resources and performance. The
analysis that follows utilized data was from Kaggle.com (1) which contained daily hospital admissions at
Hero DMC Heart institute located in the state of Punjab, India. The dataset features included details
regarding the date of admissions, date of discharge, demographics, type of admission, patient medical
history, and lab parameters. 14,825 admissions were documented over the period of April 2017 to March
2019.

__Problem Summary__

Target time series for this analysis was narrowed to three common measures of illness severity: heart
failure, shock, and mean length of stay. 

__Solution Summary__

Four kinds of time series models were applied depending on the time series to predict future values.

* ARIMA model – Autoregressive Integrated Moving Average Model

  Regression analysis which makes predictions using prior values and a moving average The model
  values are selected manually through analysis of the time series.
  
* Auto.Arima
  
  Same as above, except the model values are selected by the function through optimization.

* Lagged Auto.Arima
  
  Integrates another series lagged information to predict the target series.

* Vector Autoregression

  Explores the relationship between time series for prediction.
  
Models were iteratively tested, and appropriate statistical methods were evaluated to determine whether
or not a model could be accurately used for forecasting.

__Conclusions__

Heart Failure – The best model was a Lagged Auto.Arima (III) with Shock. The relationship
between shock and heart failure improved the model’s ability to forecast heart failure.

Shock – The best model was an ARIMA (1,0,1) with mean (I). These are low orders within the
model (ARIMA model orders can go up to 10), and the relatively simple model was able to reasonably
forecast shock behavior.

Mean Length of Stay – The best model was an Auto.Arima (0,0,2)(1,0,0) (II). Again, the orders
within the model are low. This model did include the cyclic seasonal behavior to improve prediction.

The relationships between the time series were also thoroughly explored through vector auto regression
(IV). Heart failure and shock appeared to have a relationship with each other which could be used for
future prediction.

1)  Sahani, A. (2022, January 21). Hospital Admissions Data. Kaggle.
  https://www.kaggle.com/datasets/ashishsahani/hospital-admissions-data 

_____________________________________________________________________________________________________

__Additional Information__

[Sample of Technical Report](./tsa_ctech.html)

[Sample R Code](./tsa_rcode.html)

[All Projects](./)
