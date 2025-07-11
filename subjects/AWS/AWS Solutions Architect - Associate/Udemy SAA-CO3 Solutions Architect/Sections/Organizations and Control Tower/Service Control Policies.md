AWS Service Control Policies (SCPs)

- Control the maximum available permissions
- SCPs DO NOT GRANT ANY PERMISSIONS, they only control the AVAILABLE permissions
- SCPs apply to everyone in the account - including account administrators
- Service Control Policies are found in the AWS Organizations service under "Policies"
- Users in the management account are not restricted
- For instance if you had an two OUs:
    
    - Dev
        
        - If you didn’t want DEVs to be allowed to create any instance that isn't a T2 micro you could apply a Conditional SCP limiting DEVs to only be able to run instances that are t2.micro
    - Prod