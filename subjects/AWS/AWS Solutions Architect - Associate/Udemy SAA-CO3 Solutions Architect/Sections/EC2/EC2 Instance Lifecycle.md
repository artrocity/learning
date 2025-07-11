EC2 Instance Lifecycle

- Below is the lifecycle of an EC2 Instance
    
    - Create instance, Choose AMI
    - AMI is loaded
    - Instance goes into pending state
    - Instance is now in a running state
        
        - Can reboot
            
            - Equivalent to OS Reboot
            - DNS Name and all IPv4 addresses retained
            - Does not affect billing
        - Shut Down
        - Terminate
            
            - Deleting the instance
            - Cannot recover a terminated instance
            - Root EBS volumes are deleted
        - Stop
            
            - EBS Backed instances only
            - No charge for stopped instances
            - Data charges are still being charged
            - Data in RAM is lost
            - If you start backup again, instance is migrated to a different host
            - Private IP addresses are retained, Public IPv4 addresses are released
        - Stop-Hibernate
            
            - Applies to supported AMIs
            - Contents of RAM saved to EBS volumes
            - Must be enabled for hibernation when launched
            - Specific perquisites apply