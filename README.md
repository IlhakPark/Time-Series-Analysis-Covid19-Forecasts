# Predicting new cases of COVID-19 using Time Series Analysis
Project Status: Complete

## Abstract
The end of COVID-19 guarantees tremendous opportunities in various fields, including businesses and employment; local restaurants could re-open, and temporarily laid-off airline employees could return to their workplace. According to Statista, about 413 million doses of COVID-19 vaccines had been produced up to March 2021, and China, U.S. EU, India, and U.K. are the top five countries that had produced 96% of all doses. However, these countries strictly control exportation of the vaccines for protecting their national economy. When the five countries no longer have new cases of COVID-19, the vaccines are expected to be commonly available around the world, and the pandemic is likely to end. This project applies Predictive Analytics and Time-Series Analysis, using auto.arima function in R, to predict and visualize a timeline for the end of the pandemic by determining when the COVID-19 trend stops in the five countries.

## Dataset
The COVID-19 related data is publicly available from Our World in Data. The data has 95,743 rows and 60 columns. Below is a list of columns of the data. We will clean the data and extract the relevant variables that we need to conduct the time series analysis. The new data frame will consist of location (China, U.S., EU, India and U.K.), date, from 2020-02-01 to 2021-06-01, new cases, new deaths. Since our research question is to forecast new cases and deaths of COVID-19 in the five countries, the other variables will not be used. 

## Approach

### Pre-process Data in R
Loading all the COVID-19 daily reports in R would be the first step; the reports are available in a single GitHub folder, written in csv. The rows that are not China, U.S. EU (Germany, Belgium, and Netherlands), India, and U.K., in each dataset, will be removed. Unnecessary columns will be removed and certain period of time will be selected for the study. Then, bind the datasets by country in ascending order. 

### Exploratory Data Analysis
Exploratory Data Analysis (EDA) is needed to gather insights from the dataset. First, we will check if there are gaps or missing values. In R, the str() function shows the total number of observations and its data type, and head() and tail() show the first and last five observations. The summary() function returns various summary statistics; it shows the minimum value, 1st quartile, median, mean, 3rd quartile and maximum value of the data. We can find how strong the correlation between “confirmed” and “deaths” of COVID-19. Patterns in the data must be studied. The decomposition check will allow us to study the trend, seasonality and irregular fluctuations of the dataset.

### Predictive Modeling
In order to use an autoregressive integrated moving average, or ARIMA, model, the data must be stationary, univariate and in time series data format. If the data is not stationary (have a constant mean and variance), we will have to difference the data by subtracting the next value by the current value and make the data follow a stationary pattern. Autocorrelation function (ACF) and Partial autocorrelation function (PACF) will be used to determine the parameters, auto regression, integration and moving average, of an ARIMA model. Then we will use the auto.arima function with the three parameters to return a model and predict the number of new cases and deaths of COVID-19. We will conduct different n-day forecast; we can test our model, by comparing with actual values, using 30-day forecast; we can predict the future, using 90-day forecast.

### Performance Evaluation
After a time series analysis, we can calculate the forecast error as the actual value minus the predicted value for each prediction. We can find the mean squared error (MSE) by taking the average of the squared forecast errors, then find the root mean squared error (RMSE) by square rooting the MSE. RMSE will measure the average magnitude of the error of the time series analysis. Another method to evaluate the performance of time series analysis is the mean absolute error (MAE), which can be calculated as the average of the absolute value of the forecast errors. 

### Conclusion
The ARIMA models display projection graphs forecasting new cases and deaths of COVID-19 for five countries. The main purpose of this project is to find if end of the COVID-19 is coming, with the help of vaccines. We can conclude that the pandemic will end soon if the future COVID-19 trend is downward and approaching towards zero. 

## Result
In our time series analysis, auto ARIMA function was used to determine the best combination of ARIMA parameters in terms of AIC (Akaike Information Criterion) value. Auto ARIMA also transformed the non-stationary data to stationary data. Since all countries are not in the same condition, we analyzed various combinations of the frequency of seasonality and the length of training set for each country. Four different models, that predict the number of new cases of COVID-19 after one month, were built to compare and select the best model to predict when new case number reaches to zero. In order to evaluate their measures, distance (difference), mean absolute percentage error (MAPE) and root mean squared error (RMSE) were compared.

For US, China, India and EU, the model with the closest distance has the least MAPE and RMSE. On the other hand, the UK’s second model has the least MAPE and RMSE, but the distance is not the closest. The second model was selected because there is no significant difference in the distance, but it has 26% lower MAPE and 42% lower RMSE than the third model. It is observed that all models have a better result when the training set is five months rather than 15 months.
After the COVID-19 vaccines have been produced in March 2021, all countries, except for China, have a decreasing COVID-19 trend. Based on the past five months of data, our models forecast that the spread of COVID-19 in US, India, UK and EU stops in the near future.

The predicted number of new COVID-19 cases for each country is provided below table. Our time series models predict that the COVID-19 trend in US, India, UK and EU will end in one year, three months, six months, and three months, respectively. The recent numbers of new cases in China was increasing, so the model does not forecast that the new case in China reaches zero. 

## Conclusions & thoughts
In the meanwhile, new COVID-19 virus variants are developed in some countries, and the vaccines do not work against some variants. Forecasting the pandemic is a challenging project as indefinite external factors influence its infectiousness. In the past three months, we proposed live COVID-19 related predictions for five vaccine producing countries. Our proposed time series models are selected, among various combinations, based on good levels of performance and uncertainty. The results should be more accurate if the COVID-19 trend was the same or similar as three months ago.
The pandemic may not end this year or next year as our models forecasted, due to the Delta variant. In order to improve, our models should keep track of new COIVD-19 trend and accumulate more recent data. It will eventually forecast the end of the pandemic, again, when new vaccines come out. 
