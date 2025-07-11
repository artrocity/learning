EC2 Scaling Policy

- EC2 Scaling Policy is a set of rules that determine when and how to automatically adjust the number EC2 Instances in your application.
- Instance metrics are not measured until the EC2 instance is done initializing / warming up
- There are 3 types of scaling policies in EC2
    
    - Target Tracking:
        
        - Simplest, Recommended, and Most common type
        - EC2 will track the CPU usage and when it hits a predefined threshold, it will add or remove instances based on the threshold
        - This policies goal is to maintain the target threshold
    - Simple Scaling
        
        - Works similar to a thermostat
        - When a metric goes above or below a threshold, it triggers an action. For instance, if CPU usage exceeds 75% - add 2 instances, if it drops below 25% - remove an instance
        - Cooldown period for each action type - typically 300 seconds
    - Step Scaling
        
        - Similar to simple, but you can add multiple thresholds
        - CPU 50-70% - Add one instance
        - CPU 70-90% - Add two instances
        - CPU 90%+ - Add 4 instances
    - Scheduled Scaling
        
        - Set a specific time to launch instances