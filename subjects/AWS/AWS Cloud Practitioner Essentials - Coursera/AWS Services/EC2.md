Amazon Elastic Compute Cloud

- Provides secure, resizable compute capacity in the cloud
- Compared to running on-premises servers, EC2 is flexible, cost-effective, and quick
- EC2 is basically a virtual server
- On-premises servers you have to purchase, install, secure, install OS, etc.
- AWS EC2 takes care of:
    
    - Datacenter
    - Securing the datacenter
    - Purchased the servers
    - Racked and Stacked them
    - Servers are online and ready to be used
- EC2 allows you to use whatever portion of AWS's data center that you need
- When you are done, you can turn off the instances or turn on more instances
- Pay for only what you use - i.e Running Instances
- Creating EC2 instance
    
    - When you create an instance, the virtual machine is created on the physical AWS server located in a data center.
    - EC2 Virtual Server size is partitioned automatically per your requirements
    - Servers Hypervisor manages your VM Server as well as any other VM Servers running on the physical server
    - Sharing underlying hardware is known as mulitenancy
- EC2 Configurations - Compute as a Service (CaaS)
    
    - Operating system
        
        - Windows/Linux
    - What software to run on instance
        
        - Web apps, databases, 3rd party software etc
    - Vertically scalable
        
        - Increase computing power through hardware
    - Networking configuration
    - Storage
        
        - Instance Store Volumes
            
            - Physical storage attached to the host your EC2 instance is running on
            - Since the volume is attached to the host, if you turn off the instance, all data will be deleted
            - The reason for this is because an EC2 instance is a virtual machine, the physical host could change each time you start and stop the instance
- EC2 User Responsibilities
    
    - Patching instance when a new update comes out
    - Setting up scaling of the instances
    - Architect the solutions to be available
    - Basically any management processes
 
EC2 Instance Families

- General Purpose
    
    - Jack of all trades
    - Web servers
    - Small and medium databases
- Compute Optimized
    
    - Gaming servers
    - Scientific Modeling
- Memory Optimized
    
    - Memory optimized
    - Workloads that require large amounts of data to be preloaded before running an application
- Accelerated Computing
    
    - Floating point number calculations
    - Graphics processing
    - Data pattern matching
    - Utilize Hardware accelerators
    - Application Streaming
- Storage Optimized
    
    - High performance for locally stored data
 
EC2 Pricing

- On-Demand
    
    - Only pay for the duration the instance runs for
    - Used as a baseline to determine average usage
- Savings Plans
    
    - Offers low prices in exchange for a commitment to a consistent usage in a 1 or 3 year terms
    - Up to 72% savings
- Reserved instances
    
    - Predicted usage
    - 1 or 3 year term
    - Payment options
        
        - All upfront
        - Partial upfront
        - No upfront
- Spot Instances
    
    - Spare EC2 instances
    - Amazon can claim them back
    - Batch workloads
    - 2 min warning before
    - Up to 90% off
- Dedicated hosts
    
    - Used to meet compliance requirements
    - No one will share tenancy
 
Scaling EC2

- Scalability involves beginning with only the resources you need and designing your architecture to automatically respond to changing demand by scaling in or out
- If you want scalability to automatically occur you can use AMAzon EC2 AutoScaling