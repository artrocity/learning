How to Launch an EC2 Instance

- Navigate to the AWS Console
- Searched or clicked on EC2
- Clicked Create Instance
- Named the instance
- Choose an AMI - Amazon Machine Image
    
    - Linux, Windows, SQL Server, etc.
- Select an instance type
    
    - The instance type defines the hardware profile and the cost
    - |   |   |
        |---|---|
        |T-series|General Purpose|
        |C-series|Compute optimized|
        |R-series|Memory optimized|
        |D-series|Storage optimized|
        
- Create a downloadable key pair - used for SSHing into the instance
- Networking
    
    - Choose subnets, etc
    - Create or assign to a security group
    - Enable/disable SSH
- Configure storage
- Set up any advanced options if desired
- Snapshots are taken
    
    - Snapshot is a point-in-time backup of an instance