# Mini Project on one problem statement and Solution
  ### Develop a model to forecast monthly sales for an e-commerce store based on historical sales data. The goal is to accurately predict future sales trends and identify seasonality patterns, enabling the store to optimize inventory, marketing, and business strategies.

## Python Solution for Time-Series Sales Forecasting:

## Step 1: Import necessary libraries.

    python
    
    import pandas as pd
    import numpy as np
    import matplotlib.pyplot as plt
    from statsmodels.tsa.seasonal import seasonal_decompose
    from statsmodels.tsa.statespace.sarimax import SARIMAX

## Step 2: Load and preprocess the historical sales data.

    python
    
    # Assuming 'sales_data.csv' contains the historical sales data in 'Month' and 'Sales' columns
    df = pd.read_csv('sales_data.csv')
    df['Month'] = pd.to_datetime(df['Month'])
    df.set_index('Month', inplace=True)

  ### Test data for sales_data.csv
    However, I can provide you with a sample test data in the form of a pandas DataFrame that you can use to test the solution. Please use the following code to create a test dataset:

        python
        
        import pandas as pd
        
        # Sample test data for monthly sales
        data = {
            'Month': pd.date_range(start='2022-01-01', periods=36, freq='M'),
            'Sales': [100, 120, 110, 130, 140, 150, 180, 200, 190, 210, 220, 230,
                      250, 280, 290, 300, 320, 330, 350, 380, 400, 410, 430, 440,
                      460, 480, 500, 520, 540, 560, 580, 600, 620, 650]
        }
        
        # Create a DataFrame
        df = pd.DataFrame(data)
        
        # Save the DataFrame to a CSV file
        df.to_csv('sales_data.csv', index=False)
        
        Run this code in a Python script or Jupyter Notebook to create the 'sales_data.csv' file with the sample test data. The CSV file will contain two columns: 'Month' and 'Sales', with monthly sales data for the past 36 months. You can use this file as the input to test the time-series forecasting solution.

    
## Step 3: Data Exploration and Visualization.

      python
      
      # Visualize the time-series data
      plt.figure(figsize=(10, 6))
      plt.plot(df.index, df['Sales'])
      plt.xlabel('Month')
      plt.ylabel('Sales')
      plt.title('Monthly Sales Data')
      plt.show()
      
## Step 4: Seasonal Decomposition to identify trends and seasonality patterns.

    python
    
    # Seasonal Decomposition
    decomposition = seasonal_decompose(df['Sales'], model='additive', period=12)
    trend = decomposition.trend
    seasonal = decomposition.seasonal
    residual = decomposition.resid
    
    plt.figure(figsize=(10, 8))
    plt.subplot(4, 1, 1)
    plt.plot(df['Sales'], label='Original Data')
    plt.legend(loc='upper left')
    
    plt.subplot(4, 1, 2)
    plt.plot(trend, label='Trend')
    plt.legend(loc='upper left')
    
    plt.subplot(4, 1, 3)
    plt.plot(seasonal, label='Seasonal')
    plt.legend(loc='upper left')
    
    plt.subplot(4, 1, 4)
    plt.plot(residual, label='Residual')
    plt.legend(loc='upper left')
    
    plt.tight_layout()
    plt.show()
    
## Step 5: Model Building using SARIMA (Seasonal AutoRegressive Integrated Moving Average).

    python
    
    # Build SARIMA model
    model = SARIMAX(df['Sales'], order=(1, 1, 1), seasonal_order=(1, 1, 1, 12))
    results = model.fit()
    
## Step 6: Forecast future sales.

    python
    
    # Forecast future sales
    forecast_steps = 12  # Number of months to forecast
    forecast = results.forecast(steps=forecast_steps)
    forecast_index = pd.date_range(start=df.index[-1], periods=forecast_steps + 1, closed='right')
    forecast_df = pd.DataFrame(data=forecast, index=forecast_index, columns=['Forecast'])
    
    # Plot original sales data and forecasted values
    plt.figure(figsize=(10, 6))
    plt.plot(df.index, df['Sales'], label='Original Data')
    plt.plot(forecast_df.index, forecast_df['Forecast'], label='Forecasted Sales', color='red')
    plt.xlabel('Month')
    plt.ylabel('Sales')
    plt.title('Monthly Sales Forecast')
    plt.legend()
    plt.show()
    
## Step 7: Conclusion.

    python
    
    # Print the forecasted sales values
    print("Forecasted Sales:")
    print(forecast_df)
    
# Instructions to Run the Program using Jupyter Notebook Online:

    1. Open Jupyter Notebook on your browser.
    2. Create a new Python notebook.
    3. Copy and paste the Python solution code into a new code cell.
    4. Ensure the 'sales_data.csv' file is available in the same directory as the notebook.
    5. Run the code cells sequentially to load the data, visualize the time-series, build the model, forecast sales, and display the results.

Note: To run the SARIMA model, you may need to install the 'statsmodels' library if it's not already installed. You can install it using: !pip install statsmodels.
