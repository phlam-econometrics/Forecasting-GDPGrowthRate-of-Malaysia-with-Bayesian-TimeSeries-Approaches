# Abstract
This project is for forecasting the 2025 Q2 to 2027 Q4 GDP growth rate of Malaysia.

# Introduction
The project analysed the data of Malaysia's GDP growth rate from 2015 Q2 to 2025 Q1 and forecast the GDP growth rate of Malaysia from 2025 Q2 to 2027 Q4 with Bayesian time series approaches.

# Data Source
Series: Rate of Quarterly GDP Growth & Monthly Trade by SITC Section <br/>
Period: 2015 Q2 to 2025 Q1 <br/>
Source: Malaysia's Official Open Data Portal

# Literature Review 

Forecasting Malaysia's GDP growth rate is essential for economy to plan their development and fiscal policy, a macroeconometric forecast helps analyse the economic growth of Malaysia. <br/>

Export in Malaysia has a positive effect to GDP growth and the import has a negative effect to GDP growth (Pakasa et al., 2023).<br/>

The gap of this research project is that there is lack of forecast in GDP growth rate of Malaysia in time series analysis with structural break (e.g. COVID-19 Pandemic), the prediction included the Bayesian-SARIMAX model and Holt-Winter exponential smoothing to forecast the data of GDP growth rate, with a short-term forecast of 11 quarters.

# Methodology

The data is collected from Malaysia's Official Open Data Portal. <br/>

The time series of quarterly GDP growth rate cleaned data differencing 4 lags for 4 seasons. <br/>

The Augmented Dickey-Fuller Test and Seasonally Differenced Augmented Dickey-Fuller Test are used for testing if there is any unit roots, for stationarity. <br/>

Examined Autocorrelation Function and Partial Autocorrelation Function with the original cleaned data and the differenced-4-lags data. <br/>

![Figure 1](https://github.com/phlam-econometrics/Forecasting_GDP_Growth_Rate_of_Malaysia/blob/main/GDP%20Growth%20Rate%20Forecast/output/figures/ACF_PACF_Plots.png)<br/>

According to the observation in seasonal differenced ACF and PACF, ACF is showing cuts off patterns (i.e. Spikes at lag 5 for ACF), but the PACF is seasonal significant, suggested that our model is a SARIMA process.<br/>

A Bayesian auto SARIMAX and a Bayesian manual SARIMAX process will be applied, X is the exogenous data (i.e. Cleaned data of net export data quarterly).<br/>

First, for Bayesian auto SARIMAX, with auto.arima process, the optimal result is p=4 and q=0.<br/>

Iterate 10000 times for a more accurate result<br/>

For manual Bayesian SARIMAX, based on AR(1) since it can eliminate the residual autocorrelation with capturing linear relation between GDPGrowthRate<sub>t</sub> and GDPGrowthRate<sub>t-1</sub>, and reduce the overfitting risk. <br/>

Iterate 10000 times for the Manual SARIMAX(1,0,1)(0,1,0)<sub>4</sub> <br/>

For diagnostic, applied Holt-Winters exponential smoothing, Bayesian Auto SARIMAX and Bayesian Manual SARIMAX. <br/>

With the historical data, forecasted the GDP Growth Rate of Malaysia in 2025 Q2 to 2027 Q4 through R.

# Observation

Original GDP Series p-value: 0.2328943<br/>

Seasonally Differenced GDP p-value: 0.02259342<br/>

Observed that the Augmented Dickey-Fuller Test p-value higher than 0.05, which means there are unit roots (i.e. Non-stationary), but the Seasonally Differenced Augmented Dickey-Fuller Test p-value is lower than 0.05, which means the model is stationary after differencing for 4 seasons.<br/>

Bayesian Holt-Winters: p-value = 0.0002777423<br/>

Auto-SARIMAX: p-value = 0.9571178<br/>

Manual-SARIMAX: p-value = 0.1002555<br/>

According to the result, since Bayesian Holt-Winters p value is lower than 0.05, it might not be the ideal model because it shows significant autocorrelation.<br/>

In this circumstance, Bayesian SARIMAX will be a better method to forecast the GDP growth rate.<br/>

![Figure 2](https://github.com/phlam-econometrics/Forecasting_GDP_Growth_Rate_of_Malaysia/blob/main/GDP%20Growth%20Rate%20Forecast/output/figures/Model_Diagnostics.png)<br/>

According to the QQ plot, it is observed that the prediction is reliable since the points are fall on straight line, proved the data set have a high confidence, avoided skewed datapoint and errors.

The data of Malaysia's GDP growth is seasonal, it is possibly caused by manufacturing since it is observed to have negative GDP growths (a contraction) in the first quarter of every year.<br/>

According to the export/import data of Malaysia, the manufacturing industry included machinery, mineral fuels, chemical related products etc.<br/>

Which might implies that in Malaysia, some seasons are not producing those products with reason such as shut down the massive machines for maintanence, except for the basic food, beverage factories maintain producing.<br/>

![Figure 3](https://github.com/phlam-econometrics/Forecasting_GDP_Growth_Rate_of_Malaysia/blob/main/GDP%20Growth%20Rate%20Forecast/output/figures/GDP_Forecast_Comparison.png)<br/>

With the historical data, the forecast of coming 11 lags (i.e. 11 quarters) show that the GDP growth rate of Malaysia will oscillate according to the Bayesian Holt-Winter and Bayesian auto/manual SARIMAX.<br/>

But it is possible to have a sudden rise similar to the pandemic period, but it possibly caused by the government policy<br/>

Former Case: During COVID-19 lockdown in 2020, the manufacturing industry stopped producing, after lockdown, the accumulated orders led to the rise of GDP growth rate since the production rises.<br/>

Current Case: A sudden rise of manufacturing possibly due to the new goods or the natural resources that can only be produce/extract in Malaysia, will lead to another rise of GDP growth rate.<br/>

# Suggestion

Higher input on non-manufacturing industries such as tourism can help the economy have a better performance than before, avoid having recession in some specific seasons.

# Conclusion

With the forecasting, it is possible to predict the coming 11 quarters GDP growth rate performance from 2025 Q2 to 2027 Q4, but for the period after 2027, since we do not have enough data, predicting for a longer period will lead to lower accuracy. <br/>

Although the model predicted the GDP growth rate only have slight differences compare to the pre-2020 era, but it is just built on the average prediction, with the Bayesian SARIMAX model, in fact, the potential GDP growth in Malaysia can up to 25% (based on the maximum area of three forecasting methods overlapped).

# References

https://data.gov.my/data-catalogue/gdp_qtr_real?series=growth-qoq&visual=value <br/>

https://data.gov.my/data-catalogue/trade_sitc_1d?visual=table <br/>

Pakasa, U. I., Yacob, Y., Lajuni, N., Abdillah, D. S. Z. A., & Chiat, L. W. (2023). The Impact of Domestic and External Demand Factors on Malaysia Economic Growth. International Journal of Academic Research in Business and Social Sciences, 12(1), 1057 – 1067.
