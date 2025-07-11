Cheat Sheets:  
[https://digitalcloud.training/amazon-cloudwatch/](https://digitalcloud.training/amazon-cloudwatch/)  
[https://digitalcloud.training/aws-cloudtrail/](https://digitalcloud.training/aws-cloudtrail/)￼  
Topics

- CloudWatch
    
    - Used for performance monitoring, alarms, log collection and automated actions
    - Use Cases
        
        - Collect performance metrics from AWS and on-premises systems
        - Automate responses to operational changes
        - Improve operational performance and resource optimization
        - Derive actionable insights from logs
    - Core Features
        
        - CloudWatch Metrics - services send data to CloudWatch
            
            - EC2 sends 5 minutes by default - free, 1 min chargeable
        - CloudWatch Agent send system-level metrics for EC2 and on-premises servers
            
            - System level metrics include memory and disk usage
        - CloudWatch Alarms - Monitor metrics and initiate actions
        - CloudWatch logs - centralized collection of system and app logs
        - CloudWatch Events - stream of system events describing changes to AWS resources and can trigger actions
    - Custom Metrics
        
        - Standard resolution - one minute granularity - default
        - High resolution - second granularity
    - CloudWatch Alarms
        
        - Metric Alarms - One single metric
        - Composite Alarms - Multiple alarms
    - Logs can be sent to S3 Kinesis Data Streams / Firehose
    - Unified CloudWatch Agent
        
        - Collect internal system level metrics from EC2 and on-premises
        - Retrieve custom metrics using StatsD and collectd protocols
        - Collect logs from EC2 instances and on-premises servers (Windows/Linus)
        - Agent must be installed on the server
- CloudTrail
    
    - Logs API activity
    - Retained for 90 Days
    - Cloud Trail, Trail logs any events to S3 for indefinite retention
    - CloudWatch Events can be triggered based on API calls in CloudTrail
    - Events can be streamed to CloudWatch Logs
    - Event Types
        
        - Management Events - management of resources
        - Data Events - resource operations
        - Insights - id and respond to unusual activity