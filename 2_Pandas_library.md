# Topic 2: Pandas Library

In this topic, we'll explore the Pandas library, one of the most powerful tools for data manipulation and analysis in Python. Pandas provides data structures and functions to efficiently work with structured data, making it essential for data science tasks.

Items covered:

  ## Introduction to Pandas:
        Pandas is an open-source library that provides data structures like DataFrame and Series to handle structured data effectively.
        It is built on top of NumPy, making it easy to integrate with other libraries in the scientific Python ecosystem.

  ## DataFrame:
            The DataFrame is a two-dimensional tabular data structure, similar to a spreadsheet or SQL table.
            It consists of rows and columns, and each column can have a different data type.
            Example:
    
            python
    
        import pandas as pd
    
        data = {
            'Name': ['Alice', 'Bob', 'Charlie'],
            'Age': [25, 30, 28],
            'City': ['New York', 'London', 'Sydney']
        }
    
        df = pd.DataFrame(data)

## Reading Data:

        Pandas can read data from various sources, including CSV files, Excel files, SQL databases, and more.
        Example:
    
        python
    
        # Reading from a CSV file
        df = pd.read_csv('data.csv')
    
        # Reading from an Excel file
        df = pd.read_excel('data.xlsx')
    
        # Reading from a SQL database
        import sqlite3
        conn = sqlite3.connect('database.db')
        df = pd.read_sql_query('SELECT * FROM table_name', conn)

## Data Exploration:

      Pandas provides various functions to explore data, such as head(), tail(), info(), and describe().
      Example:
  
      python
  
      print(df.head())  # Display the first few rows of the DataFrame
      print(df.info())  # Display information about the DataFrame
      print(df.describe())  # Summary statistics of numeric columns

## Data Manipulation:

        Pandas enables data manipulation tasks like filtering, selecting specific columns, and creating new columns based on existing ones.
        Example:
    
        python
    
            # Filtering based on condition
            df_filtered = df[df['Age'] > 25]
    
            # Selecting specific columns
            df_selected = df[['Name', 'City']]
    
            # Creating a new column
            df['Birth Year'] = 2023 - df['Age']
    
## Summary:
    Pandas is a powerful tool that simplifies data manipulation, cleaning, and analysis. 
    It's widely used in data science projects to handle real-world datasets. 
    Practice using Pandas to import data, explore it, and perform basic data manipulations to become proficient in data handling with Python.
