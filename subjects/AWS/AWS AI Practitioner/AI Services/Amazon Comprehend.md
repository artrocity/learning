## Amazon Comprehend
- Natural Language Processing
- Fully managed and serverless
- Uses machine learning to find insights and relationships in text
- Sample cases
	- Analyze customer interactions - emails
	- Create and group articles by topics 

## Amazon Translate
- Natural and accurate language translation
- Allows localization of content such as websites and applications

## Amazon Transcribe
 - Transcribes speech into text
 - Uses a deep learning process using automatic speech recognition (ASR)
 - Features
	 - Redaction - automatically remove PII
	 - Automatic Language Identification
- AWS Transcribe Medical
	- HIPAA compliant 
	- Can convert medical-related speech to text
	- Ability to transcribe medical terminologies
	- Supports real-time and batch transcriptions
	- Use cases:
		- Voice applications
		- Phone calls
	- Uses NLP to detect protected health information
	- Process
		- Store documents in S3
		- Analyze in real time with Firehose
		- Use Transcribe to transcribe patient narratives into text
		- Amazon Comprehend will analyze it

## Amazon Polly
- Turns speech into text
- Create applications that will talk
- Features
	- Lexicon - define how to read text such as explaining acronyms 
	- SSML - Speech Syntehsis Markup Language

## Amazon Rekognition
- Finds objects, people, text, scenes in images and videos using ML
- Facial analysis and search for user verification
- Create a database of familiar faces
- Use cases
	- Labeling
	- Content moderation
	- Text Detection
	- Face detection and analysis

## Amazon Lex
- Fully managed service to build chatbots
- Can use voice or text
- Supports multiple languages
- Integrates with Lambda, Comprehend, and Kendra

## Amazon Personalize
- ML Service to build real-time personalized recommendations
- Same tech used by Amazon.com - recommends products for you
- Implement in days, not months

## Amazon Textract
- ML service to extract text from any scanned documents such as
	- Drivers license
	- Scanned PDF, receipts, etc

## Amazon Kendra
- Fully managed document search service
- Allows you to extract answers from a document such as
	- Text, PDF, HTML, PowerPoint, MS Word
- Provides natural language search capabilities

## Amazon Mechanical Turk
- Crowdsourcing marketplace to perform simple human tasks
- Distributed virtual workforce
- Use cases:
	- Image classification
	- Data collection
	- Business Processing

## Augmented AI
- A2I
- Human oversight of machine learning predictions in production

## EC2 instances for ML
- GPU-based instances (P and G series)
- AWS Trainium
	- ML Chips used to perform deep learning on 100+ billion parameters
	- 50% cost reduction when training models
	- Trn1
- AWS Inferentia
	- ML Chips used to deliver inference at high performance and low cost
	- Inf1, Inf2
- Trn & Inf have the lowest environmental footprint

