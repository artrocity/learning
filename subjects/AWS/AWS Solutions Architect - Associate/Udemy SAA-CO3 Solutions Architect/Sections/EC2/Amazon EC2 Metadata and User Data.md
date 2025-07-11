Amazon EC2 Metadata

- Instance metadata is about your EC2 instance
- Available at [http://169.254.169.254/latest/meta-data](http://169.254.169.254/latest/meta-data)
- Two versions of Instance Metadata Service
    
    - IMDSv1
        
        - Older less secure
    - IMDSv2
        
        - Newer, more secure, and requires sessions token
    - Default EC2 Launch is IMDSv2 and may disable IMDSv1
    - Version type is chosen in Metadata Version in advanced settings
 
Amazon EC2 User Data

- Set of instructions given to an EC2 instance at its "birth"
- The instructions automatically run when the instance starts up for the first time
- User Data scripts run with root/admin privileges and can perform various setup tasks
- User Data scripts generally only run during the instance's first boot cycle only (by default)
- User Data can be enabled, given, or used via the EC2 Setup on the console or the CLI
- Limitations
    
    - Must be base64-encoded
    - Encoding is automatic with console and CLI
    - User Data is limited to 16KB before it's encoded
- Common Uses
    
    - Install software
    - Configure services
    - Setup applications
    - For instance if you were using EC2 to setup a web server, User Data could install Apache, configure it's settings, and start the service automatically