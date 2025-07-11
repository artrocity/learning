Cloud SQL

- Google's Cloud Service for Relational Databases
- You can either build your own database solution or use Google's Managed Cloud SQL
    
    - Installing SQL on a Cloud Engine VM
- Benefits of using Cloud SQL over your own database solution
    
    - Fully managed database service
    - Patches and updates are automatically applied
    - You administer SQL users
    - Cloud SQL supports many clients
        
        - Gclou sql
        - App Engine & Google Workspace scripts
        - External applications using standard MySQL drivers
    - Performance
        
        - 64 TB of Storage
        - 60,000 IOPS
        - 624 GB of RAM
        - Scale out with read replicas
    - Database choices
        
        - MySQL
        - PostgreSQL
        - Microsoft SQL server 2017 or 2019
- Cloud SQL Services
    
    - HA configuration
    - Backup service
    - Import/Export
    - Scaling
        
        - UP
            
            - Machine capacity
        - Out
            
            - Read Replicas
 
Connecting to Google Cloud SQL Instance

![Connecting to a Cloud SQL instance Yes Manual SSL Connection Cannot use SSI Connecting from outside Google Cloud Yes Need manual control over SSL certificates : No, would like • automation Authorized Networks Cloud SOL Connection Cloud SOL Auth Proxy Connecting from within Google Cloud 1 Yes Cloud SOL Private IP Google ](Exported%20image%2020250301230913-0.png)