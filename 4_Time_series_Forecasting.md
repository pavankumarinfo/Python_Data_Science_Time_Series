# Topic 4: Time-Series Forecasting

In this topic, we'll explore time-series forecasting, which involves predicting future values based on historical data patterns. Time-series forecasting is crucial for various applications, such as sales forecasting, stock market predictions, weather forecasting, and more.

Items covered:

   ## Time-Series Forecasting Basics:
        Time-series forecasting aims to predict future values in a time-dependent sequence.
        It involves analyzing past patterns and trends to make predictions about future data points.

  ## AutoRegressive Integrated Moving Average (ARIMA) Model:
        ARIMA is a popular time-series forecasting model that combines autoregression (AR), differencing (I), and moving average (MA) components.
        The AR component captures the relationship between the current observation and previous observations.
        The I component deals with differencing to transform a non-stationary time series into a stationary one.
        The MA component represents the relationship between the current observation and the residuals of past observations.

  ## Seasonal Decomposition of Time Series (STL):
        STL is a method to decompose time-series data into three components: trend, seasonality, and residuals (remainder).
        The trend component represents the underlying long-term pattern.
        The seasonality component captures the repeating patterns over fixed intervals.
        The residuals represent the noise or random fluctuations in the data.

  ## Train-Test Split:
        When working with time-series data, it is crucial to split the dataset into training and testing sets chronologically.
        The training set is used to build the forecasting model, and the testing set is used to evaluate its performance.

 ## Forecasting and Evaluation:
        After training the forecasting model, you can use it to predict future values.
        Common evaluation metrics for time-series forecasting include mean absolute error (MAE), root mean squared error (RMSE), and mean absolute percentage error (MAPE).

## Example:

  python

  ## Example: Time-Series Forecasting using ARIMA

    import pandas as pd
    import matplotlib.pyplot as plt
    from statsmodels.tsa.arima.model import ARIMA
    
   ## Load time-series data
    data = {
        'Date': pd.date_range(start='2023-01-01', periods=100, freq='D'),
        'Sales': [100, 150, 200] + [0] * 97
    }
    df = pd.DataFrame(data)
    
  ## Fit ARIMA model
    model = ARIMA(df['Sales'], order=(1, 1, 1))
    results = model.fit()
    
  ## Forecast future values
    forecast = results.forecast(steps=10)
    
  ## Plot the original data and the forecasted values
    plt.figure(figsize=(10, 6))
    plt.plot(df['Date'], df['Sales'], label='Original Data')
    plt.plot(pd.date_range(start='2023-04-11', periods=10, freq='D'), forecast, label='Forecasted Values', color='red')
    plt.xlabel('Date')
    plt.ylabel('Sales')
    plt.title('Time-Series Forecasting with ARIMA')
    plt.legend()
    plt.show()

## Summary:
    In this example, we use the ARIMA model to forecast future sales values based on the given time-series data.
    The red line represents the forecasted values for the next 10 days.
    Note that this example uses a simplified time-series dataset; in real-world scenarios, you would work with more extensive and complex datasets to make meaningful predictions.
    Understanding time-series forecasting techniques will empower you to make informed decisions and predictions in various domains where time-dependent data is essential.
