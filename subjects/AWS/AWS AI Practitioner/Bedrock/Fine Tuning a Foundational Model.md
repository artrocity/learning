# Process
- Select a model
	- Not all models can be fine-tuned
	- Must use Provisioned Throughput
- AWS provides a hosted version of that foundational model for you
- You can then adapt that model with your own data
- Fine-tuning will change the weights of the base foundational model
- Training data MUST:
	- Adhere to a specific format
	- Stored in S3

# What is instruction-based fine tuning
- Improves the performance of a pre-trained FM on domain-specific tasks
- Allows the model to be further trained on a specific task or knowledge area
- Instruction-based fine-tuning uses labeled examples that are prompt-response pairs

# Continued Pre-training
- Provide unlabeled data to continue the training of an FM
- Domain-adaptation fine-tuning to make a model an expert in a specific domain
- For example
	- Feed the entire AWS documentation to a model to make it an expert on AWS
- It's good to feed industry specific terminology into a model
- Can continue to train the model as more data becomes available

# Single Turn Messaging
- Part of instruction-based fine-turning
- system(optional): context for the conversation
- messages: an array of messages each containing:
	- role: user or assistant
	- content: content of the message

# Fine-tuning Good to know
- Re-training an FM requires a high budget
- Instruction-based fine-tuning is usually cheaper as computations are less intense and the amount of data required is less
- Requires experienced Machine Learning Engineers to perform the tasks
- You must:
	- Must prepare the data
	- Conduct o the fine tuning
	- Evaluate the model
- Running a fine-tuned model is more expensive due to provisioned throughput

# Transfer Learning
- Broader concept of reusing a pre-trained model to adapt it to a new related task
- 
