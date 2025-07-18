## What is it
- Fully managed Gen-AI Assistant for your employees
- Based on your company's knowledge and data
- Built on Bedrock, can't choose the underlying FM, uses multiple FMs
- Features
	- Can answer questions, provide summaries, generate content, and automate tasks
	- Perform routine actions: submit time off requests, send meeting invites, etc
- Use cases:
	- Write job postings
	- Create social media posts
	- Recounts of meetings from the past
- Core components:
	- Data Connectors - connects to 40 + enterprise data sources such as S3, RDS, Aurora, Salesforce, Google Drive, Gmail, Slack, Sharepoint, Office 365
	- Plugins - Allows Q Business to interact with 3rd party services such as Jira, ServiceNow, Zendesk, Salesforce
- How is it accessed
	- Users are authenticated through IAM Identity Center
	- Users receive responses generated only from the documents they have access to
	- Workflow
		- Users log in and are authenticated
			- Can login through IdP
		- Users ask questions to Amazon Q
		- Responses are limited to data that is at their permission level to access
- Admin Controls
	- Used to control and customize responses to your organizational needs
	- Admin Controls is similar to Guardrails in Bedrock
	- Can block specific words
	- Can specify it to only use internal information and no external knowledge
	- Controls can be set to:
		- Global
		- Topic - granular
- Q Apps
	- Allows you to create GenAI Powered applications without coding by using natural language
	- Leverages:
		- Companies internal data
		- Plugins
