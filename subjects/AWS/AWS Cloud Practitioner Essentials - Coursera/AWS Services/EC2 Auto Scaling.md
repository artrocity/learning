AWS EC2 Auto Scaling

- Enables you to automatically add or remove Amazon EC2 instances in response to changing application demand.
- By automatically scaling your instances in and out as needed (horizontally), you are able to maintain a greater sense of application availability
- AWS Auto Scaling has two approaches
    
    - Dynamic Scaling
        
        - Responds to changing demand
    - Predictive scaling
        
        - Automatically schedules the right number of EC2 instances based on predicted demand
 
Creating Auto Scaling

- Minimum Capacity
    
    - The number of instances that launch immediately after you create the auto scaling group
- Desired Capacity
    
    - Defaults to minimum if no desired capacity is set
- Maximum Capacity
    
    - The maximum number of instances to scale out to