AWS Directory Service

- Managed service that provides directories to organize your AWS resources, users, and permissions
- What is a directory service
    
    - A directory service stores information about objects on a network and makes this information available to users and network administrators.
    - These objects typically include users, groups, computers, printers, and other resources
    - The most common Directory service in an enterprise environment is Microsoft's Active Directory (AD)
- AWS Managed Microsoft AD
    
    - Full Microsoft AD hosted on AWS.
    - Useful for when you want the full features of AD, but AWS to handle the maintenance
    - Use Case
        
        - If your organization already uses AD and wants to extend it or move it to AWS in the cloud.
- AD Connector
    
    - A gateway or proxy to your existing on-premises Active Directory
    - Use case
        
        - Keep your AD on prem but use AWS
        - Federated sign in to AWS
            
            - You can sign in to AWS applications such as WorkSpaces, etc. with your AD sign on
        - Two Sizes
            
            - Small 500 users
            - Large 5000 users
            - Requires VPN or Direct Connect
- Simple AD
    
    - Standalone, Samba-based directory service
    - Use Case
        
        - Good choice for basic directory needs when you don't need the full feature set of AD
        - Less than 5000 users

￼Workflow

- You create the directory by specifying the Domain name and VPC
- AWS provisions two domain controllers in different AZs for high availability
- AWS maintains the domain controllers, including backups, software updates, and monitoring
- You create users and groups and set permissions
- AWS resources like Amazon WorkSpaces, RDS for SQL server, or AWS SSO can now authenticate against your directory
- This service automatically creates a trust relationship between your AWS hosted directory and your on-premises directory if you're using managed Microsoft AD with a trust configuration
 
Common Use Cases

- Extending on-premises directory to AWS
- Moving to cloud-only directory
- Enabling Single Sign On