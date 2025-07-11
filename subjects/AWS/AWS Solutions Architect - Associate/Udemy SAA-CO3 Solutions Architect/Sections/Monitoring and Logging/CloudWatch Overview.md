CloudWatch Overview

- Performance monitoring tool
- Used to trigger alarms and collect log files for collection and automated actions
- Use Cases
    
    - Collect performance metrics from AWS and on-premises systems
    - Automate responses to operational changes
    - Improve operational performance and resource optimization
    - Derive actionable insights from logs
    - Get operational visibility and insight
- Core Features
    
    - CloudWatch Metrics
        
        - Time ordered data points which are sent by services
        - Services send metrics to CloudWatch
        - EC2 sends every 5 minutes with no charge
        - Unified CloudWatch Agent - sends system-level metrics for EC2 and on-premises servers
            
            - System-level metrics include memory and disk usage - this requires unified CloudWatch Agent
        - Collect custom metrics via CLI / API
            
            - Standard resolution - 1 minute
            - High resolution - one second granularity
    - CloudWatch Alarms
        
        - Monitor metrics and initiate actions (auto-scaling)
        - Types of alarms
            
            - Metric - performs one or more actions based on a single metric
            - Composite - uses a rule expression and takes into account multiple alarms
        - Alarm States
            
            - OK - metric within threshold
            - Alarm - metric outside of threshold
            - Insufficient Data- not enough data
    - CloudWatch Logs
        
        - Centralized collection of system and app logs
        - Define expiration policies and KMS encryption
        - Send to:
            
            - S3
            - Data Streams / Firehose
    - CloudWatch Events
        
        - Stream of system events describing changes to AWS resources and can trigger actions