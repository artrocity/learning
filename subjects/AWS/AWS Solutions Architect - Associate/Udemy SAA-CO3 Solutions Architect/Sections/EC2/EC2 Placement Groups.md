AWS Placement Groups

- Methods to influence how AWS EC2 instances are physically positioned in AWS's infrastructure to optimize different performance needs
- This is similar to arranging furniture in a room - the way you position things will influence how they will work with each how and how well.
- There are 3 main types of placement groups
    
    - Cluster Placement Groups
        
        - Packs instances close together within a single AZ. This arrangement provides the lowest latency possible and highest network throughput
        - Use Cases
            
            - High performance computing applications
            - Big Data Analytics jobs that need rapid data transfer
            - Applications that need extremely low-latency communication
    - Spread Placement Groups
        
        - Each instance is placed on distinct underlying hardware in order to maximize availability
        - Use Cases
            
            - Critical applications where simultaneous hardware failures need to be avoided
            - Small groups of instances that need to stay separate
    - Partition Placement Group
        
        - Instances are grouped into logical partitions
        - Each partition runs on its own set of racks with independent power and network
            
            - Do not share the underlying hardware - each partition is on a separate rack up to 7 partitions per AZ
        - Use Cases
            
            - Large distributed and replicated workloads
            - Hadoop, Cassandra, and Kafka Deployments
            - Applications that need to manage partition awareness
    - Cluster placement groups for your trading engines where every microsecond counts
    - Spread placement groups for your critical monitoring systems to ensure they're always available
    - Partition placement groups for your data analytics systems that process market data