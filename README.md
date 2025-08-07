# CI-CD-Pipeline-for-Automated-Deployment-to-EC2-instance
Implemented an automated CI/CD workflow using AWS CodePipeline and SSM to build and deploy code to an EC2 instance on every update on Github repository.

Goals:
1. Create an EC2 instance and make it as web server.
2. Set up codepipeline by connecting with github repository.
3. Add SSM permission to codepipeline.
4. Deploy the pipeline.

Steps:

Create an EC2 instance and make it as web server by installing httpd, then attach fullaccess admin IAM role to it.

<img width="1195" height="259" alt="Screenshot 2025-07-29 at 11 32 07 AM" src="https://github.com/user-attachments/assets/ad0244f4-b36d-4c89-9161-706d0adf642c" />

Set up CodePipeline: Go to Codepipeline and go to settings to make connection to github, because application is saved in github and whenever there is changes in code, it will continously deployed in our web server. Then go to Pipelines and create pipeline, select build custom pipeline, hit next, then name the pipeline. In new service role, codepipeline will automatically create a role for us, hit next. Then choose github as our service provider, under connection select our created github connection and choose the repository where application is stored, then default branch is main. Skip build and test stage. Add deploy provider where we are going to deploy our application, in our case is Amazon EC2, in Instance type choose SSM Managed node, key - name and value - ec2 name, target directory is /var/www/html. 

<img width="1195" height="443" alt="Screenshot 2025-07-29 at 11 32 58 AM" src="https://github.com/user-attachments/assets/837dff10-43a8-4f0e-a38c-e288522fa69f" />

<img width="1075" height="311" alt="Screenshot 2025-07-29 at 11 41 46 AM" src="https://github.com/user-attachments/assets/ffe8c273-8761-4d49-b717-71fc4186e7ab" />

Add SSM permission to Codepipeline role: Go to IAM roles, select the Codepipeline created role and add SSMFullAccess to that role, then only pipeline will be deployed.

<img width="1075" height="311" alt="Screenshot 2025-07-29 at 11 43 52 AM" src="https://github.com/user-attachments/assets/22681fc0-6f56-46c7-a364-d81fe65837b4" />

<img width="1294" height="431" alt="Screenshot 2025-07-29 at 11 44 20 AM" src="https://github.com/user-attachments/assets/4113c474-cc71-4d2c-995b-712c69329f7f" />

Click Deploy

<img width="1401" height="223" alt="Screenshot 2025-07-29 at 11 44 58 AM" src="https://github.com/user-attachments/assets/ded0e9d7-0d30-4622-b76b-337bee8af51b" />
