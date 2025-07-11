Members

- 5 different type of members
    
    - Google Accounts
        
        - Represents a developer, admin, or any other person who interacts with Google Cloud
        - Accounts can be created without having to receive email to that account
    - Service Accounts
        
        - An account which belongs to an application, not a specific user
    - Google Groups
        
        - Named collection of Google Accounts and Service Accounts
        - Every group has a unique email address that is associated with the group
        - Groups are a convenient way to apply an access policy to a collection of users
    - Google Workspace Domains
        
        - Represents a virtual group of all the Google Accounts that have been created in an organizations workspace account
        - When you add a new user to your workspace domain, a new Google account is created for the user inside this virtual group
    - Cloud Identity Domain
        
        - Lets you manage users and groups using the Google Admin console
        - You will not pay for nor receive collaboration products such as Gmail, Docs, Drive, or Calendar
        - IAM Is not to be used to create or manage users or groups, this should be done through Cloud Identity or Workspace