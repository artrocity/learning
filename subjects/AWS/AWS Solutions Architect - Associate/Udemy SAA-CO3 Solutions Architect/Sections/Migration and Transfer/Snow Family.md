AWS Snow Family

- What is it:
    
    - Snow family is a collection of physical devices designed to securely transfer large amounts of data into and out of AWS, as well as to run computing workloads in locations with limited or no internet connectivity.
    - Key Components
        
        - SnowCone
            
            - Smallest Device
            - 8 TB storage
            - Built in networking
            - Ideal for edge computing, content distribution, and data collection
        - SnowBall
            
            - Midsized device
                
                - Storage optimized: 80 TB of storage
                - Compute Optimized: 42 TB of storage with more powerful compute capacities
            - Includes resources to run AWS lambda functions
            - Perfect for medium to large data migrations
        - SnowMobile
            
            - Exabyte-scale data transfer service delivered in a 45-foot long shipping container
            - Up to 100PB of storage capacity per SnowMobile
            - Designed for massive data center migrations
            - Comes with dedicated security personnel and physical security
- How it Works
    
    - Order
    - Receive
    - Connect device to network
    - Transfer data to the device
    - Return or ship the device back to AWS
    - Process the data into a designated S3 bucket or processes it as requested
- Example 1: Data Center Migration 
A media company needed to migrate 600 TB of video archives to AWS:

- Ordered multiple Snowball Edge devices
- Transferred data in parallel across devices
- Shipped devices back to AWS for upload to S3 Glacier Deep Archive
- Completed migration in two weeks versus an estimated six months over the internet