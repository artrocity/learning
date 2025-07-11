Best practices

- Leverage and understand the resource hierarchy
- Use projects to group resources that share the same trust boundary
- Check the policy granted on each resource and make sure you recognize the inheritance
- Use the principle of least privilege
- Audit policies using Google Cloud audit logs and audit memberships of groups using policies
- Grant roles to groups instead of individuals
- Control the ownership of the Google group used in IAM policies
- Service accounts
    
    - Be careful when granting the serviceAccountUser role
        
        - This is because it will grant access to everything the service account has access to
    - Establish a naming convention for service accounts
    - Establish key rotation methods and policies
    - Audit with serviceAccount.keys.list() method