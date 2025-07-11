AWS Application Migration Service

- What is it
    
    - Cloud-native service designed for lift-and-shift migrations, allowing you to quickly rehost your physical, virtual, and or cloud servers to AWS with minimal downtime. It's the primary migration service recommended for automated lift-and-shift migrations.
- How it works
    
    - Agent installation - lightweight agents on your source servers
    - Data Replications - Agents continuously replicate your source servers to a staging area in your AWS account, capturing all changes to OS, System configs, apps, and data
    - Test Launches - Before cutover, you can conduct a test to verify the apps will work properly
    - Machine Conversion - The service automatically converts your source servers to run natively on AWS
    - Cutover - When you're ready to migrate, you initiate a cutover process that creates fully functional instances from your replicated servers
    - Optimization - After migration, you can optimize your applications for cloud-native operations
- Example - A manufacturing company needs to exit their data center within 60 days
    
    - Install MGN agents on 200 + servers running Windows and Linux
    - Initiate block-level replication to AWS staging area
    - Test applications in batches to verify functionality
    - Performs coordinated cutover during a weekend maintenance window
    - Completes entire migration with less than 4 hours of downtime per application