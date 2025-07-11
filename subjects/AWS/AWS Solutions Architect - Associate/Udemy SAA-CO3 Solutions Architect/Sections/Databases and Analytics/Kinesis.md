AWS Kinesis

- Basically a highway system for real-time data, designed to handle massive amounts of info flowing continuously
- Kinesis Data Streams
    
    - Multiple lanes on the highway, each lane(shard) can handle 1mbps writes and 2mbps reads
    - Shard
        
        - Lane on the highway
        - When data comes in it's stored on the shard for 24 hours by default
        - Each shard can handle 1000 put records per second
        - If you need 5000 records per second, you need 5 Kinesis shards
    - Producers
        
        - Producers put data into the stream
        - Examples
            
            - Web Servers
            - Mobile Apps
            - IoT devices
    - Consumers
        
        - Read data from the stream
        - Examples
            
            - Lambda
            - EC2
- Kinesis Data Firehose
    
    - Firehose handles the consumption part automatically.
    - Firehouse can automatically load data directly into AWS Destinations such as:
        
        - S3
        - RedShift (Through S3)
        - OpenSearch
        - Splunk
- Firehose vs Data Streams
    
    - Firehose
        
        - Automatically scales
        - Transform data using Lambda prior to delivering it
    - Data Streams
        
        - Requires manually scaling by adjusting the total number of shards