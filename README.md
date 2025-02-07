# Home Sales Analysis with PySpark

### Project Overview
This project analyzes home sales data using Apache Spark and PySpark SQL. The dataset contains information on real estate transactions, including home prices, square footage, number of bedrooms and bathrooms, and view ratings. The analysis involves executing SQL queries to extract insights and compare performance between cached queries and Parquet-based queries.
The main objectives of this project are:
•	Process large-scale home sales data efficiently.
•	Perform SQL-based data analysis using PySpark.
•	Compare query execution performance between cached tables and Parquet storage.
•	Optimize data storage and retrieval using partitioning.
### Dataset Details
The dataset is sourced from AWS S3 and contains key fields such as:
•	date_built – The year the home was built.
•	bedrooms, bathrooms – Number of rooms.
•	sqft_living – The total living area in square feet.
•	price – The sale price of the home.
•	view – A rating based on the property’s view.
The dataset is loaded into a PySpark DataFrame, and then transformed and queried using Spark SQL.
### Analysis Performed
### SQL Queries Executed
The following SQL queries were performed to extract insights from the dataset:
1.	Average Price of 4-Bedroom Homes Per Year:
	Determines the annual average sale price of homes with four bedrooms.
2.	Average Price of 3-Bed, 3-Bath Homes by Year Built:
  Calculates the average sale price of homes with 3 bedrooms and 3 bathrooms for each year they were built.
3.	Average Price of 3-Bed, 3-Bath, 2-Floor Homes Over 2,000 sqft:
	Filters homes that meet these criteria and determines the average price.
4.	Average Price per View Rating (≥ $350,000):
	Analyzes the effect of view ratings on home prices, filtering for homes priced at or above $350,000.
5.	Performance Comparison: Cached Queries vs. Parquet-Based Queries:
	The final analysis compares query execution times between cached DataFrames and Parquet-based queries.
Performance Optimization Techniques
To enhance query execution and optimize data retrieval, the following techniques were applied:
### 1. Caching
•	The dataset was cached in Spark memory using the CACHE TABLE command.
•	This eliminates repeated computation and speeds up queries that are run multiple times.
### 2. Partitioning the Data
•	The dataset was partitioned by date_built before storing it in Parquet format.
•	Partitioning reduces the number of records scanned per query, improving performance.
### 3. Writing to Parquet Format
•	The dataset was stored in Parquet format instead of CSV.
•	Parquet supports columnar storage, which enables faster query execution.
### 4. Repartitioning Before Writing to Parquet
•	Before writing, the DataFrame was repartitioned by date_built to optimize data distribution.
•	This reduces shuffle operations and prevents Spark from generating too many small files.



## Results & Findings
•	Queries executed on cached tables are significantly faster than uncached queries.
•	Using Parquet format improves performance over CSV, as it supports efficient data compression and faster reads.
•	Partitioning by date_built improves query performance when filtering by year.
•	Repartitioning before writing to Parquet prevents excessive small files, optimizing storage.
### Next Steps & Potential Improvements
•	Explore different partitioning strategies: Instead of date_built, consider partitioning by frequently queried fields.
•	Implement bucketed tables: This can further enhance query performance by reducing shuffle operations.
•	Optimize Spark configurations: Fine-tune cluster resources and execution parameters for further efficiency.
•	Deploy on Apache Spark Cluster (AWS EMR): Running this project on a distributed Spark cluster would allow handling much larger datasets.
## Conclusion
This project demonstrates how big data processing with PySpark can be optimized using caching, Parquet format, and partitioning. The comparison of cached vs. Parquet queries highlights the importance of storage optimization and query execution planning in big data analytics.

