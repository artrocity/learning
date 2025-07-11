Kubernetes

- Open-source platform for managing containerized workloads and services
- Makes it easy to orchestrate many containers on many hosts, scale them as microservices, and deploy rollouts and rollbacks
- At the highest level, it is a set of APIs to deploy containers on a set of nodes called a cluster
- System is divided into a set of primary components that run at the control plane and a set of nodes that run containers
- Like a Restaurant manager who manages cooks
    
    - You can deploy more cooks when needed
    - Take away cooks when not needed
- How Kubernetes is ran is dictated by a deployment config file
    
    - The deployment config file is user generated
    - Kubernetes will figure out how to achieve the desired settings
 
Kubernetes Pod

- Smallest unit in Kubernetes that you can deploy
- A pod is when you deploy containers on nodes by using a wrapper around one or more containers
- Generally there is only one container per pod
- Each pod has a unique IP with configurable options