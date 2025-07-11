## What is Reinforcement Learning
- Reinforcement learning is a type of machine learning where agent will try different things in a new environment
- When it does something right, it gets a positive reward
- When it does something wrong, it gets a negative reward
- Overtime the machine agent will learn which actions leads to positive rewards and adjust it's behavior

## Types of Machine Learning Algorithms
- Supervised
	- Supervised learning is when a model is supervised by data such as labeled data
	- A model is fed labeled pictures of a car
	- When the model is then fed an unlabeled picture of a car it can recognize that it's a car
- Unsupervised
	- The model doesn't know inputs or outputs
	- It finds patterns in the data without help
	- Labels aren't provided so the machine will have to uncover the patterns itself
	- The model is fed data which is then analyzed for properties to construct patterns
- Reinforcement
	- This model uses continuous feedback provided from mining previous versions to improve itself
	- Useful for whenever the end-goal is definable, but the approach to get there can be unknown

## Reinforcement Learning Terminology
- Agent
	- Piece of software that acts autonomously to achieve a certain goal
- Environment
	- The surrounding environment that the agents interacts with
- State
	- The current position within the environment that is known to the agent
	- Essentially, what the agent can see through it's camera
- Action
	- Every state requires an action to achieve the end-goal
	- For the racer that is to complete a lap
- Reward
	- Depending on what action is taken for a given state, the agent will be rewarded with a goal
	- If the action gets the agent further towards the goal, a positive reward is given
	- If the action is unhelpful, either a negative or no reward is given
	- The reward is given by the environment and specified through a reward function

