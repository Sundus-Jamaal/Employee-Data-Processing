# Employee Data Processing

This project processes and analyzes employee records using advanced data cleaning and manipulation techniques. It showcases how to handle missing values, detect outliers, and visualize data to gain insights into employee information.

## Key Features

- **Robust Data Cleaning**: Implements various data cleaning techniques to ensure high-quality data.
- **Lambda Functions**: Uses lambda functions for efficient data transformations.
- **Cumulative Methods**: Applies cumulative methods to analyze data over time.
- **Data Visualization**: Provides visual insights into employee records using matplotlib.

## Project Overview

The project performs the following steps:

1. **Data Creation**: Simulates raw employee data with potential issues such as missing values and outliers.
2. **Data Cleaning**: Cleans the data by handling missing values, removing duplicates, and detecting outliers.
3. **Data Transformation**: Transforms data using lambda functions and applies cumulative methods for analysis.
4. **Data Visualization**: Visualizes cleaned and processed data to provide insights.

## Code Breakdown

### Step 1: Import Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

**Step 2: Create Sample Data**
```python
data = {
    'employee_id': [1, 2, 3, 4, 5, 6, None],
    'employee_name': ['John Doe', 'Jane Smith', 'Michael Brown', 'Emily Davis', 'Chris Green', None, 'Anna Bell'],
    'salary': [50000, 60000, 75000, None, 50000, 120000, 55000],
    'department': ['HR', 'Finance', 'IT', 'HR', 'Finance', 'IT', None]
}

# Create DataFrame
df = pd.DataFrame(data)
```

**Step 3: Data Cleaning**
```python
def clean_data(df):
    # Drop rows with missing employee_id
    df = df.dropna(subset=['employee_id'])
    
    # Fill missing salaries with the median value
    df['salary'] = df['salary'].fillna(df['salary'].median())
    
    # Fill missing department with 'Unknown'
    df['department'] = df['department'].fillna('Unknown')

    # Remove duplicates
    df = df.drop_duplicates()

    # Remove outliers using the IQR method
    Q1 = df['salary'].quantile(0.25)
    Q3 = df['salary'].quantile(0.75)
    IQR = Q3 - Q1
    df = df[(df['salary'] >= (Q1 - 1.5 * IQR)) & (df['salary'] <= (Q3 + 1.5 * IQR))]

    return df
```

**Step 4: Data Transformation**

```python
# Transform data with a cumulative function
df['cumulative_salary'] = df['salary'].cumsum()

# Apply a lambda function to standardize employee names
df['employee_name'] = df['employee_name'].apply(lambda x: x.strip().title() if isinstance(x, str) else x)
```

**Step 5: Data Visualization**
```python
def visualize_data(df):
    plt.figure(figsize=(10, 6))
    plt.bar(df['employee_name'], df['salary'], color='blue')
    plt.xlabel('Employee Name')
    plt.ylabel('Salary')
    plt.title('Employee Salaries')
    plt.xticks(rotation=45)
    plt.tight_layout()
    plt.show()
```

**Step 6: Main Execution**
if __name__ == "__main__":
    cleaned_data = clean_data(df)
    print("Cleaned Data:")
    print(cleaned_data)
    
    visualize_data(cleaned_data)
    ```

# Advanced Employee Data Processing

This repository contains an advanced data processing project designed for analyzing employee records, focusing on data quality and transformation techniques.

## Key Features

- **Robust Data Cleaning**: The project implements advanced data cleaning techniques to ensure high data quality for analysis.
- **Lambda Functions**: Utilizes lambda functions for efficient data transformations and standardizations.
- **Cumulative Methods**: Applies cumulative methods to analyze employee salaries over time, providing deeper insights.

## Example of Data Cleaning Techniques

- **Handling Missing Values**:
  - Fills missing `salary` values with the median of the column.
  - Fills missing `department` with `'Unknown'`.
  - Removes rows with missing `employee_id`.

- **Outlier Detection**:
  - Uses the Interquartile Range (IQR) method to detect and remove outliers in the `salary` column.

- **String Manipulation**:
  - Strips leading and trailing spaces from employee names and standardizes them to title case.

## Techniques Used

- **Pandas**: Utilized for data manipulation and cleaning operations within the project.
- **NumPy**: Used for numerical operations and handling missing data efficiently.
- **Matplotlib**: Employed for visualizing the processed data, providing insights into employee salaries.

## How to Use

You can run the employee data processing script by executing the Python file in any environment that supports Python and has the necessary libraries (such as Pandas, NumPy, and Matplotlib) installed.

1. Clone this repository or download the files.
2. Install the required libraries using pip:


### Notes
- Ensure that the formatting (especially indentation and line breaks) remains intact when you copy this into your README file.
- You can add any additional sections or information that you think would be useful for users who view your project.

    
