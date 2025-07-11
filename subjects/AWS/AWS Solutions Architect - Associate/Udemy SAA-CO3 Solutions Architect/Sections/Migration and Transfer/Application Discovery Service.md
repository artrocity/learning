AWS Application Discovery Service

- Collects server hostnames, IP addresses, MAC addresses, as well as resource allocation and utilization details of key resources including CPU, network, memory, and disk
- Agentless discovery for Virtual Servers
- Agent-based for Windows and Linux server discovery
- Discovery Connector VMware
- Data from the queries can be saved to S3 and then queried with Athena and QuickSight
- What it is
    
    - Migration planning tool that helps enterprises gather information about their on-premises data centers before migrating to AWS. It collects server hardware specifications, performance data, network connections, and application processes running on servers to provide a comprehensive view of your application infrastructure
- How it works
    
    - Installation - Deploy lightweight discovery agents on your on-premises servers or use agentless discovery through Vmware vCenter
    - Data Collection - The service collects data about
        
        - Server hardware configuration
        - Utilization metrics
        - Running processes and applications
        - Network dependencies
    - Data Storage
        
        - Information is securely stored in AWS Migration Hub Database
    - Analysis
        
        - Collected data is then used to help identify server dependencies, group resources into applications, and estimate AWS usage costs
    - Migration Planning: Use this information collected to create a migration strategy, prioritize which applications to move first, and select the appropriate AWS services.
- Example - A large financial institution with 500 + servers wants to migrate to AWS
    
    - Deploy Application Discovery Agent on their Windows and Linux Servers
    - Collects data for 30 days to capture usage pattens
    - Identifies peak usage times and dependencies
    - Creates application groups based on network connections
    - Develops a phased migration plan prioritizing non-critical applications first.