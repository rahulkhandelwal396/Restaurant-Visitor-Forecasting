# Restaurant-Visitor-Forecasting

This is a Restaurant Visitors dataset that was inspired by a Kaggle competition. The data considers daily visitors to four restaurants located in the United States, subject to American holidays. 

The dataset contains 478 days of restaurant data, plus an additional 39 days of holiday data for forecasting purposes.

The data contains an exogenous variable: holiday, which we use to get additional information about the number of people visiting restaurants during particular seasons.

### Project Flow:

<ol>
 <li>Plotting the time series data and checking for spikes during holidays.</li>
 <li>ETS decomposition of time series data.</li>
 <li>Running ADF test to check stationarity.</li>
 <li>Running auto_arima from pmdarima to get recommended orders.</li>
 <li>Splitting data into training and testing sets.</li>
 <li>Fitting SARIMA model and plotting predictions against known values.</li>
 <li>Model evaluation.</li>
 <li>Adding exogenous variable and ploting predictions on test data.</li>
 <li>Evaluating and comparing SARIMA model results with SARIMAX model results.</li>
 <li>Retraining with SARIMAX model and forecasting into the future.</li>
</ol>

### Plotting the data

The light gray lines mark occurrence of holidays.
As we can see here, generally, higher number of people visit retaurants on holidays.

<img src="restaurant_visitor_spikes.png" alt="Data"/>

### ETS decomposition

<img src="ets_decomposition.png" alt="Data"/>

We can see here that a significant amount of seasonality is present in the data.

### ADF Test

<img src="ADF test.png" alt="Data" width="400" height="300"/>

From the ADF test, we can conclude that the data is stationary.

### Running auto_arima

<img src="SARIMA.png" alt="Data" width="400" height="300"/>

This provides an ARIMA Order of (1,0,0) and a seasonal order of (2,0,0,7)

### Splitting into training and testing sets

Total length of dataset is 478 rows.
We'll assign 42 days (6 weeks) to the test set so that it includes several holidays.

Therefore, len(train) = 436; len(test) = 42

### Fitting SARIMA model and plotting predictions on test set

<img src="sarima_plotting.png" alt="Data" />

### Model evaluation 

SARIMA(1,0,0)(2,0,0,7) -> MSE Error: 1702.629477
<br>
SARIMA(1,0,0)(2,0,0,7) -> RMSE Error: 41.26293103

### Adding holiday variable; training SARIMAX model and plotting predictions on test data

<img src="sarimax_plotting.png" alt="Data" />

### Evaluating and comparing SARIMA model results with SARIMAX model results

SARIMA(1,0,0)(2,0,0,7) MSE Error: 1702.629477
<br>
SARIMA(1,0,0)(2,0,0,7) RMSE Error: 41.26293103
<br>
SARIMAX(1,0,0)(2,0,0,7) MSE Error: 965.5702335
<br>
SARIMAX(1,0,0)(2,0,0,7) RMSE Error: 31.07362601
<br>

As we can see, SARIMAX performed better than SARIMA model because of additional information about the holiday variable, which indicates spikes in the number of visitors in restaurants.

### Retraining with SARIMAX model and forecasting into the future

<img src="plotting_future.png" alt="Data" />





 
