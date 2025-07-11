There are 4 primary storage classes in Cloud Storage

- Standard Storage
    
    - Best for frequently accessed or hot data
- Nearline Storage
    
    - For data that is accessed at most once per month
    - Infrequently accessed data
    - Such as data backups, long term multimedia content, or data archiving
- Coldline Storage
    
    - Low cost option for storing infrequently accessed data
    - Coldline is different because its recommended to read or modify at most once every 90 days
- Archive Storage
    
    - Lowest cost option
    - Used for online backups, data archiving, and disaster recovery
    - Best if accessing data once per year
 
Cloud Storage can use Autoclass

- Autoclass will automatically move data into a specific class based on access patterns
- Automates class storage to save money
- Pay only for what you use
- No prior provisioning required
- Encrypts data on the server side
- Use HTTPS/TLS
 
Methods for uploading data

- Online Transfer (SDK) Gcloud Storage
- Drag and Drop option from the google console
- Storage transfer service
    
    - Allows batch transfers to upload massive amounts data
- Transfer Appliance
    
    - Connect to network
    - Load Data
    - Ship to Data Facility - Up to a petabyte