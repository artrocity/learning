Scenario 1

- Requirement
    
    - Company needs to run short batch script
- Solution
    
    - Add script to the user data of the EC2 instance

￼Scenario 2

- Requirement
    
    - Tightly coupled, HPC workload with low-latency
- Solution
    
    - Single AZ Cluster and use Elastic Fabric Adapter
 
Scenario 3

- Requirement
    
    - Business application receives weekly bursts of traffic and must scale for short periods - needs the most cost-effective solution
- Solution
    
    - Use reserved instance for minimum required workload, use spot instances for the bursts in traffic
 
Scenario 4

- Requirement
    
    - A single instance application uses a static public IP address, in the event of a failure the address must be remapped to a failover instance
- Solution
    
    - Attach an elastic IP address to an instance, remap the EIP in the event of failre