---
title : MLOps - Data Engineering
notetype : feed
date : 22-03-2022
---



#### Data Engineering
- Data Ingestion
	- Includ synthetic data generations, or data enrichment
	- Details
		- Data Sources Identifications
		- Space Estimation
		- Space Location
		- Obtaining Data
		- Backup data
		- Privacy Compliance
		- [Metadata catalog](https://dl.acm.org/doi/pdf/10.1145/2882903.2903730?download=true)
- Exploration and Validation
	- Data Profiling: Schema, data types, metadata (max, min, avg), user-defined error detectioon
	- Details
		- Use RAD tools (Jupyter noteooks) to keep records of data exploration and experimentation
		- Attribute profiling
			- Name
			- Number of records
			- Data type (categotical, numerical, int/float, text, structured, etc.) 
			- Numerical Measures (min, max, avg, median)
			- Amount of missing values (or "missing value ratio" = number of absent values / number of records)
			- Type of distribution (Gaussian, unifrom, logarithmic)
		- Label attribute identification
		- Data Visualization (Build a visual representation for value distribution)
		- Attributes Correlation: Compute and analyze the correlations between attributes
		- Additional data: Identify data would be useful for bulding the model (go back to "data ingestion")
- Data Wrangling (Cleanig)
	- Re-formatting attributes, correcting errors in data, such as missing values imputation
	- Details:
		- Transformations
		- Outliers: Fix or remote outliers
		- Missing values: Fill in missing values (e.g., withj zero, mean, median) or drop their rows or columns
		- Not relevant data: Drop attributes that provide no useful information for the task (relevant for feature engineering)
		- Restructure data: Might include the following operations
			- Reordering record fields by moving columns
			- Creating new record fields through extracting values
			- Combining multiple record fields into a single record fields
			- Filtering datasets by removing sets of records
			- Shifting the granularity of the dataset and the fields associated with records through aggregations and pivots
- Data labeling
	- Assigned into a specific category
- Data splitting (train, validation, test datasets

