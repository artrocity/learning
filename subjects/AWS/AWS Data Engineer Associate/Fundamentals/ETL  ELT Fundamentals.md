---
aliases:
  - ETL / ELT Fundamentals
---
## ETL Pipeline
- ETL stands for Extract, Transform, and Load. It's a process used for moving data to a warehouse
- Extract
	- Retrieve raw data from source systems
	- Ensure data integrity
	- Can be done in real-time or in batches
- Transform
	- Convert extracted data into a format suitable for the target data warehouse
	- Data cleanse - remove duplicates and errors
	- Data enrichments - adding data
	- Format changes - string manipulation and date formatting
	- Aggregations or computations
	- Encoding or Decoding Data
	- Handling missing values
- Load
	- Moving transformed data into a warehouse or data repository
	- Can be done in batches or streaming
	- Ensure data maintains integrity during the loading phase

## Managing ETL/ELT Pipeline
- This process must be automated in some fashion
	- This can be accomplished via AWS Glue