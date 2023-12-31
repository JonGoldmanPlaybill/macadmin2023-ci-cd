# Code Pipeline Creation Steps
 - Go to Code Pipeline->Pipelines and Create New
 - Page 1
   - Unique Name
   - Allow it to create a role
 - Page 2 - Source Stage
   - Github Version 2
   - Select existing connection or click connect to Github (follow steps in popup)
   - Select Repo
   - Select Branch
   - UNCHECK: Start Pipeline on Source Code Change (can activate when ready)
   - Artifact: Default
 - Page 3 - Build Stage
   - Build Provider: AWS CodeBuild
   - Keep Consistent Region
   - Create a new Project, POPUP:
     - Name - recommend you include 'build' in the name
     - Tag!
     - Environment image:  MANAGED IMAGE
     - Operating System: Amazon Linux 2
     - Runtime: Standard
     - Image: **MATCH BUILD x86 or arm64(aarch)** with latest release
     - Image Version: Latest
     - **PRIVILEGED: CHECK THIS FLAG**
     - Service Role: Select Existing Role created in prep - check box to allow modification
     - Additional config: LEAVE defaults
     - Buildspec: enter full path and filename to the buildspec file from the project root (*NO leading slash*)
     - Continue to CodePipline
   - Next to Deploy Stage
 - Page 4 - Deploy Stage
   - Deploy Provider:  Elastic Beanstalk
   - Select Appropriate Region, Application, and Environment

##Final Check: Does it Build & Deploy?  Check Logs for errors if not.