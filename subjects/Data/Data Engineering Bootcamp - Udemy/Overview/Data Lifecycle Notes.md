## Generation
- Identify the sources of data
	- API, External Sources, Internal Generation, Etc. 

## Lifecycle
- Ingestion
	- Numerous methods (Pull, Push, etc.)
	- Store a copy
- Transformation
	- Data is usually not in a format that you need for a unified data model
	- Transform data to your needs
	- Store a new copy
- Serving
	- Where and how do we place the data
	- How do you monitor the access to the data
	- Serve data to:
		- Machine Learning
		- Analytics
		- Reverse ETL (How do we generate our own data)
	- Store a new copy
- Storage
	- Where and how do we store the data during all of these steps
	- Store a new copy