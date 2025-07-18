What is a prompt

- A prompt is a specific instruction or question given to a computer program or user to initiate a specific action or response
 
What is Generative AI?

- Commonly Referred to as GEN AI
- Subset of AI that is capable of creating text images and other data using generative models in response to prompts
- Gen AI Models are like conversational programs that can generate content based on the inputs or prompts supplied
- Gen AI models learn patterns and structure from the input, training data, and then create new data with similar characteristics
- Gen AI has uses across a wide range of industries
- Gemini is a Gen AI Tool  
What is a Large Language Model

- Highly sophisticated computer programs
- Trained on gigantic amounts of data
- Parameters for LLM are the memories and knowledge that the machine has learned during the model training
- They determine the ability for a model to solve a problem
- General purpose means the models can solve common problems
- Saying that LLMs are pretrained means they have be trained for a general purpose with a large dataset and then fine-tuned for a specific goal with a. much smaller data set
 
How are LLMs trained?

- When you submit a prompt to an LLM, it calculates the probability of the correct answer from its pretrained model
- The probability is determined through a task called pre training
- Pre training an LLM involves feeding. A massive dataset of text, images, and code to the model so it can learn the underlying structure and patterns of the language
- Sometimes LLMs give a false or wrong answer, this is called a hallucination
- Hallucinations are words or phrases that are generated by the model that are non sensical or grammatically incorrect
- This happens because the LLM can only understand the information they were trained on
 
What is Prompt Engineering

- Prompts are text you feed to the model
- Types of prompts
    
    - Zero-shot prompts
        
        - Doesn’t provide context or samples to assist the model
    - One Shop
        
        - Provide one example to the model for context
    - Few Shop
        
        - Provide at least two examples for context to the model
    - Role Prompts
        
        - Provides a frame of reference
        - Role-playing
- Two Elements of a Prompt
    
    - Preamble
        
        - Introductory text you provide to give the model context and instructions before your main question
        - Preambles include
            
            - Context
            - Instruction/task
            - Examples (One, Few)
    - Input
        
        - The central request you're making to the LLM
- Prompt engineering is the art of figuring out what text to feed your LLM to get it to take on the behavior you want
 
Prompt Engineering Best Practices

- Write detailed and explicit instruction
    
    - Be clear and concise
- Provide boundaries for the prompt
- Adopt a persona for your input
- Keep each sentence concise
    
    - Longer sentences produce suboptimal results