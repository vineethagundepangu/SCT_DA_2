# SCT_DA_2

Task 02 - Data Cleaning and Preparation

Project Title:Data Cleaning and Preparation Using Python and Pandas

1. Project Overview

This project focuses on cleaning and preparing the Global Superstore dataset using Python and the Pandas library.

The main objective of this task is to understand the structure and quality of the dataset, identify missing values and duplicate records, correct inappropriate data types, validate the cleaned data, and prepare a final dataset for further analysis.

The complete data cleaning process was performed using Jupyter Notebook.

2. Objectives

The main objectives of this project are:

Load the dataset using Pandas.

Inspect the structure and contents of the dataset.

Identify missing values.

Handle missing values appropriately.

Identify duplicate records.

Remove duplicate records.

Check and correct data types.

Convert date columns from string format to datetime format.

Validate the cleaned dataset.

Export the cleaned dataset as a new CSV file.

3. Dataset Description

The dataset used for this project is the Global Superstore dataset.

The dataset contains information related to sales transactions, customers, products, orders, shipping, markets, regions, and financial performance.

The main columns in the dataset include:

Category

City

Country

Customer.ID

Customer.Name

Discount

Market

记录数

Order.Date

Order.ID

Order.Priority

Product.ID

Product.Name

Profit

Quantity

Region

Row.ID

Sales

Segment

Ship.Date

Ship.Mode

Shipping.Cost

State

Sub.Category

Year

Market2

weeknum

The dataset contains:

Rows: 51,290

Columns: 27

4. Tools and Technologies Used

The following tools and technologies were used in this project:

Python - Programming language used for data cleaning and preparation.

Jupyter Notebook - Environment used to write and execute Python code.

Pandas - Python library used for data loading, inspection, cleaning, and transformation.

CSV - File format used for the original and cleaned datasets.

5. Loading the Dataset

The Pandas library was imported and the Global Superstore CSV file was loaded into a DataFrame.

The following code was used:

import pandas as pd

df = pd.read_csv("Global_Superstore.csv")

After loading the dataset, the first five rows were displayed to verify that the dataset was imported correctly.

df.head()

The dimensions of the dataset were checked using:

df.shape

The output was:

(51290, 27)

This indicates that the dataset contains 51,290 rows and 27 columns.

The structure and data types of the dataset were also checked using:

df.info()

This helped identify the column names, number of records, non-null values, and data types before performing the cleaning operations.

6. Initial Data Inspection

The dataset was initially inspected to understand its structure, column names, data types, and available records.

The first five rows were displayed using:

df.head()

The dimensions of the dataset were checked using:

df.shape

The structure of the dataset was checked using:

df.info()

The data types of all columns were examined using:

df.dtypes

The initial inspection showed that most columns had appropriate data types. However, the Order.Date and Ship.Date columns were stored as string values and required conversion to datetime format.

7. Checking Missing Values

Missing values were checked using the Pandas isnull() function.

The following code was used:

df.isnull().sum()

This displayed the number of missing values in each column.

The total number of missing values in the complete dataset was calculated using:

df.isnull().sum().sum()

The result was:

0

Result

There were no missing values in the dataset.

Since every column contained complete data, no missing-value imputation or deletion was required.

This means that the dataset contained valid values for all 51,290 records across all 27 columns.

8. Checking Duplicate Records

Duplicate records were checked using the Pandas duplicated() function.

The following code was used:

df.duplicated().sum()

The result was:

0

This indicates that there were no duplicate rows in the dataset.

The duplicate records can also be displayed using:

df[df.duplicated()]

Since the duplicate count was zero, no duplicate records were present.

9. Removing Duplicate Records

Although no duplicate records were found, the duplicate removal operation was performed as part of the data cleaning process.

The following code was used:

df = df.drop_duplicates()

The dataset was then checked again:

df.duplicated().sum()

The result remained:

0

Therefore, the dataset contained zero duplicate records after the cleaning operation.

10. Checking Data Types

The data types of all columns were checked using:

df.dtypes

During the initial inspection, the following columns were identified as string values:

Order.Date

Ship.Date

These columns contain date information and therefore should be stored using a datetime data type instead of a string data type.

The other numerical and categorical columns were retained with their appropriate data types.

11. Converting Date Columns

The Order.Date and Ship.Date columns were converted from string format to datetime format.

The following code was used:

df["Order.Date"] = pd.to_datetime(
    df["Order.Date"],
    errors="coerce"
)

df["Ship.Date"] = pd.to_datetime(
    df["Ship.Date"],
    errors="coerce"
)

The errors="coerce" parameter ensures that any invalid date values would be converted to missing datetime values instead of causing the program to stop.

After conversion, the data types were checked again:

df.dtypes

The output showed:

Order.Date    datetime64[us]
Ship.Date     datetime64[us]

Therefore, both date columns were successfully converted to datetime format.

This makes the columns suitable for future date-based analysis, such as calculating delivery time, analyzing monthly sales, and identifying yearly trends.

12. Checking Missing Values After Date Conversion

After converting the date columns, the dataset was checked again for missing values.

The following code was used:

df.isnull().sum()

The total number of missing values was also checked:

df.isnull().sum().sum()

The result was:

0

Therefore, the date conversion did not introduce any missing values into the dataset.

The dataset remained complete after the data type conversion.

13. Checking the Final Dataset Shape

After completing the cleaning operations, the shape of the dataset was checked again using:

df.shape

The result was:

(51290, 27)

This means that the cleaned dataset contains:

51,290 rows

27 columns

The number of rows remained unchanged because the dataset contained no duplicate records and no records needed to be removed due to missing values.

14. Final Data Validation

A final validation summary was created to confirm the quality of the cleaned dataset.

The following code was used:

print("===== FINAL DATA CLEANING SUMMARY =====")
print("Total rows:", len(df))
print("Total columns:", len(df.columns))
print("Total missing values:", df.isnull().sum().sum())
print("Total duplicate rows:", df.duplicated().sum())
print("Order.Date data type:", df["Order.Date"].dtype)
print("Ship.Date data type:", df["Ship.Date"].dtype)

The final output was:

===== FINAL DATA CLEANING SUMMARY =====
Total rows: 51290
Total columns: 27
Total missing values: 0
Total duplicate rows: 0
Order.Date data type: datetime64[us]
Ship.Date data type: datetime64[us]

Final Validation Results

Data Quality Check

Result

Total Rows

51,290

Total Columns

27

Missing Values

0

Duplicate Rows

0

Order.Date

datetime64

Ship.Date

datetime64

The validation confirms that the dataset was successfully cleaned and prepared.

15. Data Cleaning Summary

The following data cleaning operations were completed:

Cleaning Operation

Result

Dataset Loading

Completed

Initial Data Inspection

Completed

Missing Value Check

0 missing values

Missing Value Handling

No action required

Duplicate Check

0 duplicates

Duplicate Removal

Completed

Data Type Check

Completed

Date Conversion

Completed

Final Dataset Validation

Completed

The final dataset is complete and suitable for further analysis.

16. Exporting the Cleaned Dataset

After completing the cleaning and validation process, the cleaned dataset was exported as a new CSV file.

The following code was used:

df.to_csv("Global_Superstore_Cleaned.csv", index=False)

The cleaned dataset was saved as:

Global_Superstore_Cleaned.csv

The index=False parameter was used so that the Pandas DataFrame index would not be added as an extra column to the exported CSV file.

The cleaned CSV file contains the final prepared dataset.

17. Key Findings

The main findings from the data cleaning process are:

The Global Superstore dataset contains 51,290 rows and 27 columns.

No missing values were found in any of the columns.

No duplicate records were found.

The duplicate removal operation was applied successfully.

The Order.Date column was successfully converted from string format to datetime format.

The Ship.Date column was successfully converted from string format to datetime format.

No missing values were introduced during the date conversion.

The final dataset contains 51,290 rows and 27 columns.

The cleaned dataset was successfully exported as Global_Superstore_Cleaned.csv.

18. Conclusion and Project Files

Conclusion

The Global Superstore dataset was successfully cleaned and prepared using Python and Pandas in Jupyter Notebook.

The dataset initially contained 51,290 records and 27 columns. A detailed data quality check was performed to identify missing values and duplicate records. The analysis showed that there were no missing values and no duplicate records in the dataset.

The Order.Date and Ship.Date columns were initially stored as string values. These columns were converted into datetime format to make them suitable for future date-based analysis.

After completing the cleaning, transformation, and validation steps, the final dataset contained 51,290 rows and 27 columns, with zero missing values and zero duplicate records.

The cleaned dataset was exported as Global_Superstore_Cleaned.csv and is ready for further data analysis, data visualization, statistical analysis, and predictive modeling.

Project Files

The project folder contains the following files:

Task02/
│
├── Task02_Data_Cleaning.ipynb
├── Global_Superstore.csv
├── Global_Superstore_Cleaned.csv
└── README.md

File Descriptions

Task02_Data_Cleaning.ipynbContains the complete Python code used for loading, inspecting, cleaning, validating, and exporting the dataset.

Global_Superstore.csvThe original Global Superstore dataset used for the cleaning process.

Global_Superstore_Cleaned.csvThe final cleaned dataset generated after completing the data cleaning and preparation process.

README.mdContains the project documentation, methodology, data cleaning steps, results, and conclusion.

Author

Task 02 - Data Cleaning and Preparation

Programming Language: Python

Library: Pandas

Environment: Jupyter Notebook

Dataset: Global Superstore
