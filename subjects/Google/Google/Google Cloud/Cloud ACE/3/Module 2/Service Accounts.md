Service Account

- Belongs to application not an individual
- Used to carry out service-to-service interactions
- Convenient when not accessing user data
- Tokens are used to access any service API in your project
- Programs running within Compute Engine instances can automatically acquire access tokens with credentials
- Identified by an email address
- Assigned when created
- 3 types of service accounts
    
    - User-created (Custom)
        
        - Use IAM Roles for Permissions and Policies
    - Built-in
        
        - Compute Engine default service account
            
            - Automatically created per project
            - Granted Project Editor Role
            - Can edit via Access Scopes under Identity and API access
    - Google APIs service account
        
        - Runs internal Google processes on your behalf
- Two types of service account keys
    
    - Google Managed
        
        - All service accounts have google managed keys
        - Google stores both the private and public portion of the key
    - User-Managed
        
        - Google doesn’t save user-managed keys