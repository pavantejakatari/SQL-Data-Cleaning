SQL Data Cleaning: Global Layoffs Dataset

This project is a hands-on exercise in cleaning real-world data using MySQL. I worked with the Kaggle Layoffs 2022 dataset, which tracks global layoffs across companies, industries, and countries.

The main goal was to take raw, messy data and transform it into a clean and reliable dataset ready for analysis.


Steps I Followed

1. Created a Staging Table

Kept the original raw data untouched.

Built a staging table to perform all cleaning tasks safely.


2. Removed Duplicates

Used ROW_NUMBER() with PARTITION BY to detect duplicate rows.

Transferred data into a second staging table with row numbers.

Deleted rows where row_num > 1 to keep only unique records.


3. Standardized Data

Industry column: Replaced blanks with NULL and filled them in by matching other rows of the same company.

Standardized inconsistent values, e.g. Crypto Currency → Crypto.

Country column: Fixed trailing punctuation (e.g. United States. → United States).

Date column: Converted from text (mm/dd/yyyy) to proper DATE format.


4. Handled Null Values

Left legitimate NULLs in columns like total_laid_off and funds_raised_millions untouched, since they represent missing real-world data.

Deleted rows where both total_laid_off and percentage_laid_off were NULL (not useful for analysis).


5. Final Cleanup

Dropped the helper row_num column once duplicate handling was done.

Verified that the dataset was consistent, standardized, and analysis-ready.


What I Learned

How to use window functions for duplicate detection.

The value of staging tables to avoid corrupting raw data.

Practical strategies to handle nulls, blanks, and inconsistent values.

Converting messy text fields into proper SQL data types.


Tools Used

MySQL Workbench for queries and cleanup.

Kaggle dataset as the raw input source.


Next Steps

With the data cleaned, the next phase would be:

Exploratory data analysis (EDA) to uncover trends in layoffs.

Building dashboards to visualize industry and country impacts.

Comparing layoff patterns across company stages and funding levels.


Repo Structure

data/ → Raw dataset (CSV)

sql_scripts/ → All SQL queries used for cleaning

README.md → Project overview (this file)


This was a solid exercise in developing a data cleaning mindset in SQL—systematically removing duplicates, fixing inconsistencies, and making the data trustworthy for deeper analysis.
