AWS Athena

- Allows to run SQL queries on data against data such as Data Lake on S3
- Prevents the need for loading data from S3 into a database prior to querying it
- Query data in CSV, TSV, JSON, Parquet, and ORC formats
- Pay for amount of data scanned by each query
- Using columnar formats like parquet can dramatically reduce costs
- Partitioning data by date can make queries more efficient
 
AWS Glue

- Used as a metadata catalog
- Preforms 3 functions
    
    - Crawling - Glue crawlers examine your data in S3
        
        - Charge by the minute
    - Cataloging - Information discovered by the crawlers gets stored into the catalog
        
        - This catalog is like a reference book that Athena can use to understand your data's structure
        - Generous free tier
    - ETL - Glue can transform your data. If your logs are in JSON but you need them in Parquet, you can use Glue to handle the transformation
        
        - Billed by the second
 
AWS Athena and Glue Workflow
 
1. Store raw data in S3
2. Glue crawlers discover and catalog the data structure
3. Athena uses Glue catalogs to know how to read and query the data
4. You can now analyze terabytes of data using SQL queries