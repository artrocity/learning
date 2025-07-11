**Hierarchy**
 
Google Cloud's Hierarchy contains 4 levels, starting from the ground up they are:

- Resources
    
    - Virtual Machines
    - Cloud Storage Buckets
    - Tables in Big Query
    - Anything else in Google Cloud
    - Resources are organized into projects
- Projects
    
    - Projects can be organized into folders and subfolders
    - Projects have 3 Identifying Attributes
        
        - Project ID
            
            - Assigned by Google Cloud
            - Globally Unique
            - Mutable during creation
            - Immutable After Creation
        - Project Name
            
            - Need not be unique
            - Chosen by the user
            - Mutable
        - Project Number
            
            - Globally Unique
            - Assigned by Google Cloud
            - Immutable
    - Projects are the basis for enabling and using Google Services
        
        - Managing APIs
        - Enabling Billing
        - Adding and removing collaborators
        - Adding or Removing Services
    - Projects are separate entities under the Organization Node
    - Projects hold resources which belong to that project alone
    - Projects can have different owners and users because they are billed and managed separately
- Folders
    
    - Folders let you assign policies to resources at a level of granularity you choose
    - Folders require an Organization Node which is the top most layer
    - Can contain Folders, Projects, or a combination of both
    - Folders can have administrative rights that differ from other folders so they can operate individually
    - All resources within a folder share the same rights
    - Use folders to group projects under an organization in a hierarchy
    - For example you may have the following hierarchy
        
        - Organization Node
            
            - Legal (Folder)
                
                - Legal Resources
            - Finance (Folder)
                
                - Finance Resources
            - HR (Folder)
                
                - HR Resources
- Organization Node
    
    - Encompasses all the Projects, Folders, and Resources
 
The resource hierarchy directly relates to how POILICES ARE MANAGED AND APPLIED on Google Cloud
 
Resource Manager Tool

- API
- Gathers a list of all projects
- Create new projects
- Update projects
- Delete projects
- Recover deleted projects
- Access through RPC API and REST API￼

**Policies**
 
- Can be applied at the project, folder, and organization node level
- Some google cloud services can be applied at the resource level as well