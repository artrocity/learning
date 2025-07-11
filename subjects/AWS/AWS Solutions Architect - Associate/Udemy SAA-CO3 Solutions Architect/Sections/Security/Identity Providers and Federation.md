Identity Providers & Federation

- Web Identity Federation
    
    - What it is
        
        - Web Identity Federation allows users to sign in using well-known external identity providers (IdPs) such as Google, Facebook, Amazon, or any OpenID Connect OIDC compatible provider.
    - How it works
        
        - User authenticates with a web IdP (Like Google)
        - IdP returns a token to the user's app or browser
        - Token is exchanged for a temporary AWS credential via AWS Security Token Service (STS)
        - Temporary credentials allow access to permitted AWS resources
    - Example
        
        - You have an S3 buckets and want to allow users to upload photos to it
        - Instead of creating an individual IAM user for each user, you allow them to sign in with their Google Account
        - When they authenticate with Google, your app exchanges the Google Token with a temporary AWS STS credential that only permit's uploads to a specific location in the bucket
- SAML Federation
    
    - What it is
        
        - Security Assertion Markup Language (SAML) 2.0 federation connects enterprise identity systems like Microsoft AD or Okta to AWS
    - How it works
        
        - A user attempts to access the AWS CLI
        - They're redirected to their organizations Identity System
        - After authenticating, the Identity system generates a SAML assertion (Digitally signed XML document)
        - Assertion is sent to AWS, which validates and provides access
    - Example
        
        - Large corporation with thousands of employees use Microsoft AD for identity management.
        - With SAML 2.0 federation, employees can sign in once to their corporate network (Single Sign on) and then access AWS resources without a separate login.
        - Their corporate identity determines which AWS resources they can access and IT admins manage permissions centrally
- Amazon Single Sign-On
    
    - Rebranded to IAM Identity Center
- IAM Identity Center
    
    - What it is
        
        - Acts as a central Hub for SSO across multiple AWS accounts and applications
    - How it works
        
        - It can connect to existing identity sources ( Active Directory, External IdPs, or It's own directory)
        - Administrators define permissions set that determine access levels
        - Users get a personalized portal showing just the AWS accounts and applications they can access
    - Example
        
        - A company has multiple AWS accounts for different departments and environments (dev, testing, prod).
        - Rather than managing IAM users in each account, they use IAM Identity Center.
        - Their employees go to a single portal where they see only the accounts and apps they're authorized to use.
        - When they click on an account, they're automatically signed in with the appropriate permissions
    - IAM Identity Center in Detail
        
        - Key components
            
            - Identity Source - Where user IDs come from (AD, IdPs, IAM Identity Center)
            - Permission Sets - Collections of policies defining what actions users can perform.
            - Assignments - Connect users or groups to specific AWS accounts with specific permission sets