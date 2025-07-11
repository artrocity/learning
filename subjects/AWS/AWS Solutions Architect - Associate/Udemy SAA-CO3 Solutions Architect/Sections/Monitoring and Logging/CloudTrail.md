AWS CloudTrail

- CloudTrail logs API activity for auditing
- Notifications can be sent to SNS when CloudTrail publishes log files
- Management events are logged and retained for 90 days
- CloudTrail Trail logs can be stored in S3 for indefinite retention
    
    - Can enable log file integrity validation - checks for tampering
- Trail can be within Region or all regions
- CloudWatch Events can be triggered based on API calls in CloudTrail
- Events can be streamed to CloudWatch logs
- Cloud Trail Events:
    
    - Management Events - provide information about management operations performed on resources
    - Data Events - Provide information about the resource operations performed on or in a resource
    - Insight Events - Identify and respond to unusual activity associated with API write events.