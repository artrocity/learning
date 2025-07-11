## What is prompt engineering
- Prompt gives guidance and leaves a lot to the model's interpretation
- Prompt engineering = Developing, designing, and optimizing prompts to enhance the output of FMs for your needs
- Improved Prompting consists of 4 tasks:
	- Instructions
		- Task for the model to perform
	- Context
		- External information to guide the model
	- Input data
		- The input for which you want a response
	- Output indicator
		- The output type or format

## Negative Prompting
- Technique which specifies what the model should not include
- Negative prompting assists in:
	- Avoid Unwanted Content
		- Explicitly states what not to include
	- Maintain Focus
		- Helps the model stay on topic
	- Enhance clarity
		- Prevents the use of complex terminology

## How text is generated in an LLM

### Prompt Probability
- The roads were __fill_in_the_blank_
- AI will run a probability of the word that will be generated and could be wet, flooded, muddy, blocked etc. Each word has a probability assigned to it and is picked at random based on the probability

### Prompt Performance Optimization
- System Prompts
	- How the model should behave or reply "You are a teacher for AWS", etc
- Temperature
	- Controls randomness of the AI's choices
	- Lower = more predictable text
	- Higher = more creative and varied text
	- Usually set between 0.7-1.0 for balanced output
- Top P
	- Limits choices to tokens that add up to probability P
	- Helps avoid very unlikely words
	- Works well with Temperature to control randomness
	- Usually set around 0.9
- Top K
	- Keeps only the K most likely next words
	- Creates a hard limit on choices
	- Often used with Top P for tighter control
	- Usually set around 40
- Using Together
	- Temperature first decides how random the choices are
	- Top P then filters based on probability
	- Top K adds a final limit on number of options
	- Lower all three for factual, consistent outputs
	- Raise them for creative, varied outputs
- Length:
	- Maximum length of the answer
- Stop Sequences
	- Tokens that signal the model to stop generating content
- Prompt Latency
	- How fast the model responds
	- Impacted by:
		- Model size
		- Model itself
		- Number of token inputs
			- bigger = slower
		- The number of tokes in the output
			- bigger = slower
	- NOT IMPACTED BY:
		- Top P, Top K, Temperature

## Prompt Engineering Techniques
- Zero-shot prompting
	- Present a task without providing training for that task
	- No context, input
	- Rely fully on the model's general knowledge
- Few-shots prompting
	- Provide examples of the task to guide the model
	- Provide a few shots to the model to perform the task
- Chain of thought prompting
	- Divide the task into a sequence of reasoning steps
	- Use a sentence like think step by step
	- Helpful when solving a problem as a human usually requires several steps
	- Can be combined with other methods
- RAG - Retrieval Augmented Generation
	- Combine model with external data sources to generate a more informed response

## Prompt Templates
- Simplify and standardize the process of generating prompts
- Helps with
	- Process user input text
	- Orchestrates between FM, action group, and knowledge bases
	- Formats and returns responses to the user
- Can be used with Agents
- Inputs are inserted into the prompt template which is sent to the user model

## Prompt Template Injections
- Users could try to enter malicious inputs to hi-jack our prompt and provide information on a prohibited or harmful topic
- Protection includes:
	- Add instructions to ignore unrelated or malicious content