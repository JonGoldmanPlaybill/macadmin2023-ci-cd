# Steps for Creating Elastic Beanstalk Environment for Deploy

 - In EB Open Applications and Click on your Application (or create one)
 - Click on Create Environment
 - Page 1
   - Environment Tier: Web Server
   - Application Name should already be filled out, add Tags!
   - Create an environment name that makes sense (your EC2 Instances will be named this too!)
   - Platform Type: Managed
   - Platform: Docker
   - Branch: Docker on Amazon Linux 2
   - Platform Version: Take the recommended
   - Application Code: Sample Application
   - **Configuration Presets: Custom Configuration**
 - Page 2
   - Service Role: Let EB Create a new one
   - EC2 Key Pair: Select your preconfigured key pair
   - EC2 Instance Profile: Select your role that you pre-created
 - Page 3
   - VPC: Select your default VPC (or one you have created)
   - Instance Settings: Activate Public IP (even if you don't use it)
   - Instance Subnets: Check off *at least* 2 subnets (don't include us-east-1e)
   - **RDS/Database Not Recommended as part of EB**
   - Tag Again!
 - Page 4
   - Accept Instance defaults
   - Apply any custom security groups
   - Capacity: Select Load Balanced, even if one server.  Accept Defaults down to next.
   - Architecture:  Match your planned deploy, recommend arm64
   - Research and choose instance types, start with Micro
   - Load balancer defaults should be good, can add SSL listener if you like (change Load Balancer later to redirect non-ssl to ssl)
 - Page 5
   - Remove Managed Updates (recommended)
   - Can change rolling updates percentage if you have more than 1 server
   - All other defaults should be fine for basic use
 - Page 6
   - SUBMIT! (and crossed fingers never hurt)

## Checks and other changes before Code Pipeline:
 - Attach to the environment (open in a web browser and make sure you see the default app)
 - Go into EC2->Load Balancers and make any rule/listener changes
 - Go into Route53 and create an Alias to your ALB in a domain
 - Click on your ALB CNAME and make sure it works to serve the test app