GKE or Google Kubernetes Engine

- Managed Google Kubernetes environment in the cloud
- Consists of multiple machines
    
    - Specifically Compute Engine Instances - Grouped together to form a cluster
- GKE is different from Kubernetes because it's simpler
- GKE manages all the control plane components for us
- FKE exposes an IP address, which we send all of our API requests, but GKE takes responsibility for provisioning and managing all the control plane infrastructures behind it
- Eliminates the need for a separate control plane
- GKE has different modes
    
    - Autopilot
        
        - Recommended
        - GKE manages underlying infrastructure such as node config, autoscaling, auto-upgrades, baseline security configurations, and baseline network configs
        - Optimized for production
        - Helps produce strong security posture
        - Promotes operational efficiency
    - Standard Mode
        
        - The user manages the underlying infrastructure
        - Same functionality as Autopilot, however you are responsible for the configuration, management, and optimization of the cluster
- To create a Kubernetes cluster with GKE, you can use the Google Cloud Console or the gcloud command in the Cloud SDK