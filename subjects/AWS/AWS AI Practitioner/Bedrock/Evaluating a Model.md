# AWS Bedrock Model Automatic Evaluation
- Evaluate a model for quality control
- Built-in task types:
	- Text-summarization
	- Question and Answer
	- Text classification
	- Open-ended text generation
- Bring your own prompt data set or use built-in curated prompt sets
- Score are calculated automatically

# How it works
- Prepare Benchmark questions and answers
- Send benchmark questions to a model to evaluate
- Evaluated Model will generate answers
- Automated Evaluation
	- A Judge model will compare the evaluated model's answers vs your provided benchmark answers and create a score. 
- Human Evaluation
	- Employees (Subject Matter Experts) will define the metrics and values used to measure the responses

# Why is it important
- Curated collections of big data are designed specifically at evaluating the performance of language models over a wide range of topics, complexities, and linguistic phenomena
- These "benchmark" data sets are vita to help measure the accurate, speed, efficiency, and scalability of a particular model.
- Benchmark datasets can be used to very quickly detect any kind of bias and potential discrimination against a group of people

# Model Evaluation Metrics
- Metrics for automated evaluation
	- ROUGE - Recall-Oriented Understudy for Gisting Evaluation
		- Evaluate automatic summarization and machine translation sytems
			- ROUGE-N: measure the number of matching n-grams between reference and generated text
			- ROUGE-L: longest common subsequence between reference and generated text
		- BLEU Bilingual Evaluation Understudy
			- Evaluates the quality of the generated text, especially for generated text
			- Considers the precision and penalizes too much brevity
			- Looks at a combination of n-grams(1,2,3,4)
		- BERTScore
			- Semantic similarity between generated text
			- Uses pre-trained BERT models to compare the contexualized embeddings of both texts and computes the cosine similarity between them
			- Capable of capturing more nuance between the texts
		- Perplexity:
			- How well the model predicts the next token
- Business Metrics to Evaluate Models On:
	- User Satisfaction
		- Gathers users' feedback and assess their satisfaction with the model response
	- Average Revenue Per User
		- Average Revenue per user attributed to the Gen-AI app
	- Cross-Domain Performance
		- Measure the model's ability to perform cross-domain tasks
	- Efficiency
		- Evaluate the model's efficiency in computation, resource utilization, etc.
