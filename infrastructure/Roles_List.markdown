# List of Preset Settings, Roles & Permissions
## Elastic Beanstalk
 - EC2 Role Policies
   - AmazonEC2RoleforSSM
   - AWSElasticBeanstalkWebTier
   - AWSElasticBeanstalkEnhancedHealth
   - EC2InstanceProfileForImageBuilderECRContainerBuilds
 - EC2 Key Pair
   - Create One!

## Code Deploy Role
 - Create New Policy: Allow all read for Secrets
 - Create New Role for Codebuild and attach:
   - New Secrets Policy
   - AmazonEC2ContainerRegistryFullAccess AWS Policy