---
layout: default
---

## Cardiac Hospital Admissions - Technical Report Heart Failure ###

Below is an excerpt from the full technical report (available upon request). The included section focused on heart failure which was the hardest time series to capture and provides a snapshot into the general process/evaluation for each variable explored. 

__Introduction__

Medical time series present a unique opportunity for time series analysis. Exploring admissions
data can provide insight into the demands placed on healthcare teams, hospital resources and
performance. The analysis that follows utilized data was from Kaggle.com (1) which contained daily
hospital admissions at Hero DMC Heart institute located in the state of Punjab, India. The dataset
features included details regarding the date of admissions, date of discharge, demographics, type of
admission, patient medical history, and lab parameters. 14,825 admissions were documented over the
period of April 2017 to March 2019. Target time series for this analysis was narrowed to three common
measure of illness severity: heart failure, shock, and mean length of stay.

__Pre-processing__

Pre-processing for the dataset was extensive. The original date of admission feature had
numerous varying input discrepancies which had to be corrected manually. Data was de-identified. Factor
and numeric variables were converted to their appropriate type for data exploration. Non-target features
with a high volume of NA’s were removed for this application. Instances with a remaining high volume of
NA’s were removed. Date of admission was converted to a date using as.Date from the library lubridate.
Following an initial data exploration (detailed in the following section), three time series objects of the
target variables were created. Heart failure and shock were aggregated by sum daily. Length of stay was
aggregated daily by mean – becoming mean length of stay. All-time series were trimmed to 725 as the end
of the time series revealed further entry errors in the source data. All models were built with these
trimmed time series including vector auto regression from the start of the project, as not using the
trimmed time series resulted in forecasting errors.

__Data Exploration__

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/663fdf3a-cc42-4c59-997f-bb5888fae50d)

Figure 1: Left - Duration of Stay & Heart Failure, Right - Duration of Stay & Shock

The aim of the initial data exploration was to provide additional context for the target time series. Box plots were used in addition to summary statistics to investigate the overall distribution of the target variables with regards to duration of stay. 
The distribution of positive heart failure was higher and wider than non-heart failure patients, suggesting that patients with heart failure stayed longer than those without (fig. 1, left). The distribution of positive shock patients is lower and wider than those without shock. Finally, outcome and duration of stay distributions were plotted. While outcome is not the focus
of this analysis it can still give a strong indication of the severity of illness on the unit. 

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/6156e60d-7fd4-4e97-8d01-d86fdb5b6643)

Figure 2 displays the boxplots for the three outcomes – discharged against medical advice (DAMA, n = 896), discharge (n = 13756) and expiry (n = 1105). The outcome of admission for a majority of individuals within this dataset was discharge.

__Analysis – Individual Time Series__

_Heart Failure_

The heart failure time series appeared additive, with drift and an increasing trend as evidenced by the decomposition plot (figure 3).There was a strong seasonality visually present which ranged in magnitude from -1.0 to 1.5.

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/4691d931-ca41-4e5b-ad68-1bbdfb8f386d)
Figure 3: Decomposition of Heart Failure TS

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/9b32e8dd-b93d-4a93-86bd-8881139296f4)
Figure 4: ACF & PACF of Heart Failure

The ACF (fig.4, left) of the heart failure time series show significant autocorrelation, with seasonal scalloping and a slow taper indicative of an AR process. The PACF (fig.4, right) also shows significant
autocorrelation, some seasonal scalloping, and a more rapid taper indicative of an MA process. The EACF of the time series has a top row of x’s and a first column of x’s suggestive of infinite processes. The KPSS test rejects the null hypothesis with a p-value of 0.01, 
indicating the series is non-stationary. The Augmented Dickey Fuller test also rejects the null hypothesis with a p-value of 0.01 indicating the series is stationary. The two tests do not agree.

An Arima 1,0,1 with drift was fitted. Seasonality was iteratively tested but was not found significant and did not result in model improvements. The AIC of this model was 3715.61, the BIC was
3738.46. All coefficients tested significant at the 0.05 significance level. The ACF of the residuals showed only one small autocorrelation, and the Ljung – box test failed to reject the null
hypothesis with a p-value of 0.785. The auto.arima selected a ARIMA (1, 1, 1) model with an AIC of 3717.69 and a BIC of 3731.41. Inspection of the ACF of the difference suggests that over differencing may
be occurring. Back testing was performed on both models. ARIMA (1,0,1) with drift had an RMSE of 3.27 and a MAE of 2.55. ARIMA (1, 1, 1) had an RMSE of 3.28 and a MAE of 2.57. The
difference in MAE/RMSE of these two models was minimal. Considering the concern of over differencing – the ARIMA (1,0,1) was selected for forecasting. The plotted forecast displays the upward trend and
captures the movement occurring with the time series (figure 5).

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/4833811c-365b-4328-9b5b-d43cd39e08d9)
Figure 5.  Forecast of ARIMA (1,0,1) with drift on Heart Failure

# Conclusions & Future Work #

The top model for each of the time series is detailed in table 1 below: 

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/730d2ce7-7473-4615-9c5f-9f6b83098ce1)


The model with the lowest AIC/BIC and best overall performance was the ARIMA(1,0,1) with mean model for shock. The heart failure time series proved the trickiest to capture. While the lagged auto.arima with shock was an improvement on prior models, the AIC/BIC/RMSE/MAE of this model still remained higher
than the other time series models. The complexity of the underlying time series, the disagreement within the KPSS/Dickey-Fuller tests, the over differencing indicated etc. all worked to make this the hardest time series to capture. Analyzing medical time series datasets proved a unique challenge. Leveraging time
series analysis would be crucial to better understand hospital resources, staffing demand, patient population and more. 

These datasets are rich in insight; indeed, many more analyses could be completed with the dataset used for this report. Future analysis could examine the other time series, more deeply explore the relationship between features and integrate the environmental factors.

LINK TO SELECTED R CODE
[Back](./tsa_cardiac.html)
