AWS Elastic MapReduce (EMR)

- Service for processing and analyzing massive amounts of data
- It uses a cluster of computers called nodes
- Nodes work together, with each one handling a portion of the overall task
- EMR works with popular Big Data Frameworks such as:
    
    - Apache Hadoop:
        
        - Coordinates how work gets distributed and making sure all the pieces come back together correctly
    - Apache Spark
        
        - Faster modern framework that keeps more data in memory
    - Apache Hive
        
        - Allows you to write SQL queries to analyze your data
- Workflow
    
    - Create a cluster
        
        - Specify how many master (supervisor), core(main work force), and task (extra help for temp workloads) nodes you want
    - Submit your data processing job
- Use cases:
    
    - Processing millions of transactional records
    - Identifying buying patterns
    - Generate personalized recommendations
    - Calculate inventory predictions