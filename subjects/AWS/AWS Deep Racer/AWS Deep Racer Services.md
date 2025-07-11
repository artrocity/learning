## AWS Services Used to Power Deep Racer
- SageMaker
	- Assists in preparing, building, training, and deploying machine learning models
	- SageMaker is used to train the Deep Racer Model
- RoboMaker
	- Complete cloud solution to simulate, test, and securely deploy robotic applications at scale
	- RoboMaker provides the simulation environment for Deep Racer
- S3
	- Object storage sercice
	- Deep Racer stores models inside S3
- CloudWatch
	- Monitoring and observability service
	- Collects monitoring and operational data in the form of logs
	- CloudWatch stores logs about your Deep Racer Models
	- You can use to analyze to refine your model
- Kinesis Video Streams
	- Service to securely stream video from connected devices to AWS for analytics, machine learning, and other playbacks
	- Kinesis video streams is used to stream simulated video that RoboMaker environment generates into the Deep Racer Console


![[Pasted image 20250315094020.png]]