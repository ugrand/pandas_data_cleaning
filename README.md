# pandas_data_cleaning
Data cleaning is a crucial step in data analysis and involves preparing the dataset for further processing. In Python, the pandas library is commonly used for data manipulation and cleaning. Below is an example of how you can clean a dataset using pandas.
Data cleaning is a crucial step in data analysis and involves preparing the dataset for further processing. In Python, the pandas library is commonly used for data manipulation and cleaning. Below is an example of how you can clean a dataset using pandas.

First, ensure you have pandas installed. You can install it using pip:

bash
Copy code
pip install pandas
Let's consider a sample dataset that might contain common issues like missing values, duplicate entries, and inconsistent formats. We'll go through each of these issues and see how to clean them using pandas.

python
Copy code
import pandas as pd
import numpy as np

# Sample data
data = {
    'Name': ['Anna', 'Bob', 'Cathy', 'Dave', 'Eva', 'Finn', 'Anna'],
    'Age': [28, np.nan, 22, 29, 25, None, 28],
    'City': ['New York', 'Los Angeles', 'New York', 'new york', 'Paris', 'Paris', None]
}

# Create DataFrame
df = pd.DataFrame(data)

# Display the original DataFrame
print("Original DataFrame:")
print(df)

# 1. Handling Missing Values
# Option 1: Fill missing values with a specific value or a computed value
df['Age'].fillna(df['Age'].mean(), inplace=True)  # Filling missing ages with the mean age

# Option 2: Drop rows with missing values
df.dropna(subset=['City'], inplace=True)  # Dropping rows where City is missing

# 2. Removing Duplicates
df.drop_duplicates(subset=['Name', 'City'], inplace=True)  # Dropping duplicates based on Name and City

# 3. Standardizing Text Data
df['City'] = df['City'].str.title()  # Capitalizing the first letter of each word in City

# 4. Other common data cleaning operations might include:
# - Converting data types (e.g., converting strings to datetime)
# - Splitting columns
# - Merging data from different sources
# - Implementing more complex functions to clean specific types of data (e.g., regular expressions for text)

# Display the cleaned DataFrame
print("\nCleaned DataFrame:")
print(df)
This script demonstrates a few common data cleaning operations:

Handling Missing Values: You can either fill missing values with a specific value or a computed value (like the mean of the column), or you can choose to drop rows or columns with missing values.

Removing Duplicates: The drop_duplicates method is used to remove duplicate rows from the DataFrame. You can specify which columns to consider for identifying duplicates.

Standardizing Text Data: Often, text data comes in various formats. In this example, the city names are standardized to have the first letter of each word in uppercase.

Other Common Operations: Depending on the dataset, you might need to convert data types, split or merge columns, or apply more complex functions to clean specific types of data.

This example is quite basic and designed for demonstration purposes. Real-world datasets often require more sophisticated cleaning based on the specific nuances of the data.
