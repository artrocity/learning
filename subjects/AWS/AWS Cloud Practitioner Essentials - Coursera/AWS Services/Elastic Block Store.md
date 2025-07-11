Amazon Elastic Block Store

- EBS Volumes or virtual hard drives can be created and attached to your EC2 instances
    
    - These drives are separate from the local drives on the physical host of an EC2
    - This allows data to persist between start and stops of the EC2 instance
- EBS allows Snapshots or incremental backups of your data
    
    - It is advised to regularly take snapshots
    - The first snapshot taken copies all of the data, each subsequent backup only the blocks of data that have changed are saved
- EBS Volumes store data in a single availability zone
- To attach an EBS to an EC2 instance both the EC2 and the EBS volume must reside within the same AZ (Availability Zone)