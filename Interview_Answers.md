# Task 1 – Interview Questions and Answers

## 1. What are missing values and how do you handle them?
Missing values are fields for which no value is recorded. I first identify them using `df.isnull().sum()` and check the percentage of missing data. I then choose a treatment based on the column and business context: remove a row only when appropriate, fill numeric data with a mean or median, or fill categorical data with a mode or an explicit category. In this task, missing `income` values are filled with the median because income can be skewed and the median is less affected by extreme values.

## 2. How do you treat duplicate records?
I identify exact duplicates using `df.duplicated().sum()` and remove them with `df.drop_duplicates()`. I also check whether customer IDs repeat. I do not automatically delete repeated IDs because they may represent separate valid records; I inspect them and apply the business rule before removing anything.

## 3. Difference between `dropna()` and `fillna()` in Pandas?
`dropna()` removes rows or columns containing missing values, depending on its parameters. `fillna()` replaces missing values with a specified value or strategy, such as a median, mean, mode, or forward fill. `dropna()` can reduce the dataset size, while `fillna()` preserves records but introduces an estimated or replacement value.

## 4. What is outlier treatment and why is it important?
Outlier treatment means identifying and deciding how to handle unusually high or low observations. Outliers can affect averages, visualizations, and some machine-learning models. I can detect them with the IQR method, box plots, or z-scores. I investigate them before removing or capping them because some extreme values are genuine customer behavior.

## 5. Explain the process of standardizing data.
Standardizing data means making values consistent in format and representation. Examples include trimming extra spaces, using consistent capitalization for category labels, standardizing column names, and converting dates to one format. For numerical machine-learning features, standardization can also mean scaling values to a common scale, such as z-score scaling; that is a separate modeling step from cleaning text formats.

## 6. How do you handle inconsistent data formats (e.g., date/time)?
I inspect the source format, parse values with Pandas using an explicit format or options such as `dayfirst=True`, and convert them to datetime. I use `errors='coerce'` to expose invalid dates as `NaT`, then count and review those values. I export dates in a consistent format such as `YYYY-MM-DD`.

## 7. What are common data cleaning challenges?
Common challenges include missing values, duplicate records, inconsistent category labels, incorrect data types, invalid dates, outliers, inconsistent units, and ambiguous business rules. Another challenge is deciding whether an unusual value is an error or a valid observation. I document each decision so the process is reproducible.

## 8. How can you check data quality?
I check row and column counts, data types, missing-value counts, duplicate counts, unique category values, valid ranges, and date parsing results. I also use summary statistics and sample records to detect unexpected values. After cleaning, I repeat the checks and confirm that the output file is saved correctly.

## Short project explanation for an interview
“I used Pandas to clean the Customer Personality Analysis marketing dataset. I inspected its structure and data types, standardized column names, identified missing values, filled missing income values with the median, removed exact duplicate rows, normalized text fields, and converted the customer enrollment date to datetime. I also checked numeric types and flagged potential invalid values and outliers for review. Finally, I exported the cleaned dataset to CSV and documented the steps so the process can be repeated.”
