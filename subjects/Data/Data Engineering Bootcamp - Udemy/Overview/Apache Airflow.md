## What is it?
- Open-source tool for orchestrating complex workflows and data pipelines, centered around certain key concepts
	- Directed Acyclic Graph
		- The foundational concept in Airflow. A DAG is a collection of all the tasks you want to run in an organized way.
		- DAG is a method to manage tasks
	- Task
		- Tasks represents a unit of work within a DAG
		- Each task is an instance of an Operator
		- Operators determine what actually gets done. 