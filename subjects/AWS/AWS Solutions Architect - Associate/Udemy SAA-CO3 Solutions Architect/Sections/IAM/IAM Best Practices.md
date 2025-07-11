IAM Best Practices

- Requires workloads to use temporary credentials with IAM roles to access AWS
- Require MFA for all accounts
- Rotate access keys regularly for use cases that require long-term credentials
- Safeguard your root user credentials and don’t use them for everyday tasks
- Apply principle of least-privilege to users and applications
- Get started with AWS Managed policies and move toward least-privilege permissions
- Use IAM Access Analyzer to generate least-privilege policies based on access activity
- Regularly review and remove unused users, roles, permissions, policies, and credentials
- Use conditions in IAM policies to further restrict access
- Verify public and cross-account access to resources with IAM Access Analyzer
- Use IAM Access Analyzer to validate your IAM policies to ensure secure and functional permissions
- Establish permissions guardrails across multiple accounts
- Use permissions boundaries to delegate permissions management within an account