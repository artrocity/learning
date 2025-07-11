# Retrieval-Augmented Generation (RAG)

## TLDR

Retrieval - Retrieves data from outside of it's knowledge base (data it was trained on)
Augmented - Augments this retrieved data with the original query
Generation - Generates a response based on the "Augmented Prompt"

## Core Concept

- Combines the knowledge from foundation models with external data sources
- Allows LLMs to access and reference information beyond their training cutoff
- Helps reduce hallucinations by grounding responses in factual, retrievable content

## How RAG Works

1. **Query Processing**:
    - User submits a query or prompt
    - The system converts this query into a vector representation (embedding)
2. **Retrieval**:
    - The system searches a knowledge base (vector database) for relevant information
    - Similar vectors/documents are retrieved based on semantic similarity
    - This retrieval happens before the LLM generates its response
3. **Augmentation**:
    - Retrieved context is combined with the original prompt
    - This "augmented prompt" provides the LLM with relevant information
4. **Generation**:
    - The LLM generates a response using both its pre-trained knowledge and the retrieved context
    - The response is grounded in the specific information from your knowledge base

## Analogy
- Think of RAG like taking an open-book test instead of relying solely on memory. The LLM can "look up" specific information in your documents before answering, making responses more accurate and up-to-date.

## Vector Database
- Workflow
	- S3 External Data -> Document Chunks -> Embedded Model -> Vector Database
- Database options
	- OpenSearch - Default
		- Search & Analytics database, real time similarity queries
		- Ability to store millions of vector embeddings
		- Scalable Index Management
		- Fast Nearest-neighbor search capability
	- Amazon DocumentDB - MongoDB Compatible
		- Real time similarity queues, store millions of vector embeddings
	- Aurora
		- Relational database, proprietary to AWS
	- RDS
		- Relational database - open source
	- Graph Database
		- Neptune
	- MongoDB
	- Redis
	- Pinecone
- Embeddings Model
	- Amazon Titan
	- Cohere
	- Document Chunks

## RAG Data Sources
- S3
- Confluence
- SharePoint
- SalesForce
- Web pages
- More added over time...

## Bedrock RAG use cases
 - Customer Service Chatbot
	 - Knowledge base - products, features, specifications, troubleshooting, and FAQs
	 - RAG application - chatbot that can answer customer queries
- Legal Research and Analysis
	- Knowledge Base - laws, regs, case precedents, legal opinions
	- RAG App - chatbot
- Healthcare Question
	- Knowledge base - diseases, treatments, etc
	- Rag application - chatbot