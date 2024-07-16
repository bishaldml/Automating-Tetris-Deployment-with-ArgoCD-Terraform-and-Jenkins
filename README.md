# Automating-Tetris-Deployment-with-ArgoCD-Terraform-and-Jenkins
Automating Tetris Deployment with ArgoCD, Terraform, and Jenkins | By Mr. Cloud Book

# Prerequisites:
1. AWS Account: To get started, you’ll need an active AWS account. Ensure that you have access and permission to create and manage AWS resources.
2. AWS CLI: Install the AWS Command Line Interface (CLI) on your local machine and configure it with your AWS credentials. This is essential for managing your AWS resources.
3. IAM User and Key Pair: Create an IAM (Identity and Access Management) user with the necessary permissions to provision resources on AWS. Additionally, generate an IAM Access Key and Secret Access Key for programmatic access. Ensure that you securely manage these credentials.
4. S3 Bucket: Set up an S3 bucket to store your Terraform state files. This bucket is crucial for maintaining the state of your infrastructure and enabling collaboration.
5. Terraform: Install Terraform on your local machine. Terraform is used for provisioning infrastructure as code and managing AWS resources. Make sure to configure Terraform to work with your AWS credentials and your S3 bucket for state storage.

## STEP-1: Creating a EC2 instance with Following configuratiions using Terraform.
##### Creating a new user
1. Goto IAM Dashboard.
2. click on users
3. click on 'Create user'
4. Give the User name: bishal
5. Tick on 'Provide user access to AWS management console'
6. Tick on 'I want to create an IAM user'
7. Click on Next
8. click on Attach policies directly.
9. For now give AdministratorAccess (Note we use necessary ec2 and eks permission only on org, but for learning purpose now we use the full admin permission)
10. Click on Next
11. click on 'Create user

##### Creating an access key for the above created new user.
1. Select the newly created user for the IAM user dashboard.
2. Click on 'Security Credentials'
3. Create access key
4. Select "CLI" and confirm it.
5. next
6. Create access key and download the .csv file to use later.

##### Creating EC2 instance and other aws resources using Terraform.
#### Clone this repo: https://github.com/Aj7Ay/Tetris-V1.git
1. Open the clone repo with vs-code IDE.
2. cd Jenkins-CICD
```
terraform init
terraform validate
terraform plan
terraform apply
Or,
terraform apply --auto-approve (provide this cmd only if you are sure for your code to run sucessfully)
```
### *Note: You need to install the terraform on your local machine to run the above tf commands.


## STEP-


## STEP-


## STEP-



## STEP-




## STEP-
