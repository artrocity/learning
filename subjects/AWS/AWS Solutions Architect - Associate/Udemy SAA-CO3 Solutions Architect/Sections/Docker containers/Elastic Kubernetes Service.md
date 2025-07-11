AWS EKS

- Managed service for running Kubernetes applications
- Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications
- Kubernetes allows the standardization of container orchestration across multiple environments (GCP, Azure, AWS, On-Premises) using a managed Kubernetes implementation
- Features
    
    - Hybrid Deployment
    - Batch processing
    - Machine Learning
    - Web Apps
- Managed Kubernetes services run on EC2 / Fargate / AWS Outposts
- Pods
    
    - Groups of containers
- Scaling
    
    - Cluster Auto Scaling
        
        - Vertical Pod Autoscaler
        - Horizontal Pod Autoscaler
    - Workload Auto Scaling
        
        - EKS Supports two autoscaling projects
            
            - Cluster Autoscaler - uses AWS Scaling Groups
            - Karpenter open source autoscaling - works with EC2 fleet