Network Interfaces

- The primary network interface for an EC2 instance has a private IP address and an optional public IP
- You can have multiple network adapters connected to an instance
- Elastic Network Interfaces can be attached from subnets within the same AZ
- You can not attach ENIs from subnets in different AZs
 
Elastic Interfaces and Adapters

- Elastic Network Interface
    
    - Basic adapter for when there are no high performance requirements
    - Can be used with all instance types
- Elastic Network Adapter
    
    - Enhanced networking performance
    - Higher bandwidth and lower inter-instance latency
    - Must choose an instance type that supports ENA
- Elastic Fabric Adapter
    
    - Use with High Performance Computing (HPC), MPI, and ML use cases
    - Tightly Coupled Instances
    - Can use with all instance types