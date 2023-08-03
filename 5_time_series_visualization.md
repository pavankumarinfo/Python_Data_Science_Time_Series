# Topic 5: Time-Series Visualization

In this topic, we'll explore time-series visualization techniques to gain insights from time-dependent data. Visualizing time-series data is essential for identifying patterns, trends, and anomalies, enabling better understanding and decision-making.

Items covered:

  ## Line Plot:
        Line plots are a simple and common way to visualize time-series data.
        They display data points as connected line segments, showing the data's trend over time.
        Example:

        python

    import pandas as pd
    import matplotlib.pyplot as plt

    # Assuming df is a DataFrame with 'Date' and 'Sales' columns
    plt.plot(df['Date'], df['Sales'])
    plt.xlabel('Date')
    plt.ylabel('Sales')
    plt.title('Time-Series Line Plot')
    plt.show()

## Scatter Plot:

    Scatter plots can be useful when you want to visualize the relationship between two time-series variables.
    They display data points as individual dots without connecting lines.
    Example:

    python

    # Assuming df is a DataFrame with 'Date' and 'Temperature' columns
    plt.scatter(df['Date'], df['Temperature'])
    plt.xlabel('Date')
    plt.ylabel('Temperature')
    plt.title('Time-Series Scatter Plot')
    plt.show()

## Seasonal Decomposition Plot:

    Seasonal decomposition plots help visualize the trend, seasonality, and residuals in time-series data.
    They provide insights into the underlying patterns and fluctuations.
    Example:

    python

    import statsmodels.api as sm

    # Assuming df is a DataFrame with 'Date' and 'Sales' columns
    decomposition = sm.tsa.seasonal_decompose(df['Sales'], model='additive')
    decomposition.plot()
    plt.show()

## Rolling Statistics:

    Rolling statistics involve calculating measures like moving averages and rolling standard deviations.
    They help smooth out noise in time-series data and highlight underlying trends.
    Example:

    python

    # Assuming df is a DataFrame with 'Date' and 'Sales' columns
    rolling_mean = df['Sales'].rolling(window=7).mean()
    plt.plot(df['Date'], df['Sales'], label='Original Data')
    plt.plot(df['Date'], rolling_mean, label='7-Day Rolling Mean', color='red')
    plt.xlabel('Date')
    plt.ylabel('Sales')
    plt.title('Rolling Mean Time-Series Plot')
    plt.legend()
    plt.show()

## Multiple Subplots:

    When visualizing multiple time-series data on the same plot, using multiple subplots can improve clarity.
    Each subplot focuses on a specific aspect of the data.
    Example:

    python

        # Assuming df is a DataFrame with 'Date', 'Sales', and 'Temperature' columns
        fig, (ax1, ax2) = plt.subplots(2, 1, figsize=(10, 8))

        ax1.plot(df['Date'], df['Sales'])
        ax1.set_ylabel('Sales')
        ax1.set_title('Time-Series Sales Plot')

        ax2.plot(df['Date'], df['Temperature'], color='orange')
        ax2.set_xlabel('Date')
        ax2.set_ylabel('Temperature')
        ax2.set_title('Time-Series Temperature Plot')

        plt.tight_layout()
        plt.show()

## Summary:
    Time-series visualization provides valuable insights into data patterns and relationships over time. 
    Utilize these visualization techniques to explore and understand your time-series datasets effectively.
