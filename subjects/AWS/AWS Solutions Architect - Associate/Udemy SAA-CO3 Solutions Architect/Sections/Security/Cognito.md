AWS Cognito

- Cognito is AWS's comprehensive identity management service that handles, authentication, authorization, and user management for web and mobile applications
- It's essentially the door keeper and membership database for your digital applications
- Cognito consists of 2 core components:
    
    - User Pools
        
        - User Pools are directories that provide sign-up and sign-in options for your application users. They function as a complete IdP solution with robust features
        - A User Pool stores user profile information and handles:
            
            - User registration and account creation
            - Sign in with username/password or social identity providers
            - Built in custom user profile attributes
            - MFA
            - Account recovery flows
            - Email and Phone Verification
            - Advanced security features like adaptive auth
        - Users sign in to a user pool and then they receive a JSON Web Tokens (JWTs)
            
            - 1.) ID token that contains identity information
            - 2.) Access tokens for API access, and refresh tokens
            - 3.) Refresh Tokens for obtaining new tokens without re-authentication
    - Identity Pools
        
        - Also called Federated Identities provide temporary AWS credentials for accessing AWS services directly from client applications. This allows you to:
            
            - Securely access AWS resources from client-side code
            - Support multiple identity providers, including Cognito user pools
            - Set fine-grained permissions based on user identity
            - Create guest and unauthenticated roles
        - Identity pools don't store user profile information, they translate external identities into AWS credentials through a process called "credential vending"
- How It works - Auth Flow
    
    - User Registration and Authentication
        
        - A new user registers with your application through Cognito User Pools
        - Cognito sends a verification through either SMS or EMAIL and handles the confirmation process
        - Upon sign-in Cognito validates the credentials and issues JWTs (ID, Access, Refresh)
        - These tokens can be used to access your apps and APIs
    - AWS Resource Access
        
        - The app sends the user pool tokens to Cognito Identity Pools.
        - Identity Pools exchange these tokens for temporary AWS credentials
        - These credentials have permissions defined by IAM roles
        - The application uses these credentials to directly access AWS services like S3 or DynamoDB
    - Token Refresh
        
        - When tokens expire, the application uses refresh tokens to get new access tokens
        - This happens transparently to the user, maintaining their session
- Example:
    
    - Imagine building an Instagram like app, where users upload photos to a S3 Bucket
    - Registration and Auth
        
        - User downloads app and creates an account with email and password
        - Cognito User pool handles the verification email and account creation
        - User logs in and receives auth tokens
    - Photo Upload Process
        
        - User takes photo in app
        - App exchanges user pool tokens for temporary S3 credentials via Identity pool
        - App uploads photo directly to S3 using these credentials
        - Each user only has access to their own photo folder in S3