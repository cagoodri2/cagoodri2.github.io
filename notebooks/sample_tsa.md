#Author: Corissa Goodrich

#Project: Time Series Analysis Cardiac Admissions

#The following is a sample of project code. 

#Load Libraries

    library(lubridate)
    library(ggplot2)
    library(forecast) 
    library(ggfortify)
    library(fBasics)
    library(tseries)
    library(fpp2)
    library(lmtest)
    library(astsa)
    library(forecast)
    library(TSA)
    library(stats)
    library(tidyr)
    library(dplyr)
    library(xts)

#SAMPLE OF TIME SERIES ANALYSIS & MODELING

    #Heart Failure
    heart_fail = aggregate(x = as.numeric(as.character(admit$HEART.FAILURE)), FUN = sum, by = list(D.O.A. = admit$D.O.A))
    heart_ts = ts(heart_fail$x[1:725], frequency = 30)
    head(heart_ts)
    autoplot(heart_ts)
    decomp = decompose(heart_ts)
    plot(decomp)

    acf(heart_ts)
    pacf(heart_ts)
    eacf(heart_ts)
    acf(diff(heart_ts))

#KPSS/ADF test

    kpss.test(heart_ts) #non-stationary
    adf.test(heart_ts) #stationary 


    fit1_heart = Arima(heart_ts, order=c(1,0,1), seasonal = c(0,0,1))
    fit1_heart
    coeftest(fit1_heart)
    acf(fit1_heart$residuals)
    Box.test (fit1_heart$residuals, type = "Ljung-Box")

    fit2_heart = auto.arima(heart_ts, seasonal = TRUE)
    fit2_heart
    coeftest(fit2_heart)
    acf(fit2_heart$residuals)
    Box.test (fit2_heart$residuals, type = "Ljung-Box")

    source("backtest.R")
    back1 = backtest(fit1_heart, orig = 700, rt = heart_ts, h = 5)
    back2 = backtest(fit2_heart, orig = 2017, rt = heart_ts, h = 24)

    autoplot(forecast(fit1_heart, h=24)) #appears to accurately represent the behavior

#CROSS CORRELATION & lag2.plot
    cor(mean_stay$x[1:725], heart_fail$x[1:725])
    cor(mean_stay$x[1:725], shock$x[1:725])
    cor(heart_fail$x[1:725], shock$x[1:725]) #most highly correlated from the three

    lag2.plot(stay_ts, heart_ts, 5) 
    lag2.plot(stay_ts, shock_ts, 5)
    lag2.plot(shock_ts, heart_ts, 5) 

    linear <- lm(heart_ts ~ shock_ts, data = admit)
    summary(linear)
    skewness(linear$residuals) #moderate positive skew
    kurtosis(linear$residuals) #heavy tails
    autoplot(linear)

#lag zero

    ccf(heart_fail$x[1:725], shock$x[1:725])

#SAMPLE LAGGED AUTO.ARIMA
    detach("package:dplyr", unload=TRUE)
    lag_fit= auto.arima(lag(heart_ts,0), xreg = shock_ts)
    summary(lag_fit)
    coeftest(lag_fit)
    acf(lag_fit$residuals)
    Box.test(lag_fit$residuals, type = "Ljung-Box")
    autoplot(lag_fit)
    summary(fit1_heart)
    autoplot(fit1_heart)

    back7 = backtest(lag_fit, orig = 555, rt = heart_ts, h = 10)

    autoplot(forecast(fit1_heart, h=24))
    autoplot(forecast(lag_fit, xreg = shock_ts))

#SAMPLE VAR.R VECTOR AUTOREGRESSIVE MODELS

    autoplot(decompose(heart_ts))
    autoplot(decompose(shock_ts))

    VARselect((cbind(heart_ts, shock_ts)), lag.max = 8, type = 'const')

##investigate lag 4, 7

    fit1_var = VAR((cbind(heart_ts, shock_ts)), p = 4, type ='const')
    fit2_var = VAR((cbind(heart_ts, shock_ts)), p = 7, type = 'const')

    serial.test(fit1_var, lags.pt = 10, type = "PT.asymptotic")
    serial.test(fit2_var, lags.pt = 10, type = "PT.asymptotic")#better

    coeftest(fit1_var)
    coeftest(fit2_var)
