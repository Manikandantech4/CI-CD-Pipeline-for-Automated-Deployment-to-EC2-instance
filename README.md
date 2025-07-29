# CI-CD-Pipeline-for-Automated-Deployment-to-EC2-instance
Implemented an automated CI/CD workflow using AWS CodePipeline and SSM to build and deploy code to an EC2 instance on every update on Github repository.

Goals:
1. Run an EC2 instance and make it as web server.

Steps:

Create an EC2 instance and make it as web server by installing httpd, then attach fullaccess admin IAM role to it.

Set up CodePipeline: Go to Codepipeline and go to settings to make connection to github.
