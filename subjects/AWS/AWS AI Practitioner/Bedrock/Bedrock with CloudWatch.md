## CloudWatch
- Model Invocation Logging
	- Send logs of all invocations to AWS CloudWatch or / and S3
	- Can include text, images, and embeddings.
	- Allows you to further analyze and build alert options thanks to CloudWatch Log insights
- CloudWatch Metrics
	- Published metrics from Bedrock to CloudWatch
		- Including "ContentFilteredCount", which helps to see if Guardrails are functioning
		- Can build CloudWatch Alarms on top of the metrics