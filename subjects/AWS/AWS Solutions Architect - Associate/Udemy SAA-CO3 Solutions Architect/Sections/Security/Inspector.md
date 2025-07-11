AWS Inspector

- Runs assessments to check for security exposures and vulnerabilities in EC2 and Lambda
- Configured to run on a schedule
- Agent must be installed for EC2
- Network Assessments
    
    - Network assessments do not require agents
    - Assessments are network config analysis that check for ports reachable from outside the VPC
    - If the inspector agent is installed on your EC2 instances, the assessment also find processes reachable on port
    - Price based on the number of instance assessments
- Host Assessments
    
    - Assessments: Vulnerable software, host hardening, and security best practices
    - Requires an agent