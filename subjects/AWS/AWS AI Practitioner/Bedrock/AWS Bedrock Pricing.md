## Pricing Options - AWS Bedrock
- On-Demand
	- Pay as you go
	- Text Models - Charged for every input/output token processed
	- Embedding Model - For every input token processed
	- Image Models - for every image
	- Base Models only
- Batch mode:
	- Multiple predictions at a time
	- Can provide up to 50% discount
- Provisioned Throughput
	- Purchase Model units for a certain time period
	- Throughput - Max number of input output tokens processed per minute
	- Works with Base, Fine-Tuned, and Custom Models

## Model Improvement Costs Order
- Prompt Engineering
	- Very cheap no additional computing needed
- Retrieval Augmented Generation
	- Uses external knowledge
	- No FM Changes, no additional computation
- Instruction-based fine-tuning
	- FM is fine-tuned with specific instructions
	- Requires additional computations
- Domain Adaptation Fine-Tuning
	- Model is trained on a domain-specific dataset
	- Intensive computations

## Cost Savings - Bedrock
- On-Demand - great for unpredictable workloads, no long term commitment
- Batch - up to 50% discounts
- Provisioned - allocated capacity, no savings
- Temperature, Top K, Top P - no impact
- Model Size - smaller the model, cheaper the price
-  Main driver of cost is the number of input / output tokens