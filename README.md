# Automating-Tetris-Deployment-with-ArgoCD-Terraform-and-Jenkins
Automating Tetris Deployment with ArgoCD, Terraform, and Jenkins | By Mr. Cloud Book

# Prerequisites:
1. AWS Account: To get started, you’ll need an active AWS account. Ensure that you have access and permission to create and manage AWS resources.
2. AWS CLI: Install the AWS Command Line Interface (CLI) on your local machine and configure it with your AWS credentials. This is essential for managing your AWS resources.
3. IAM User and Key Pair: Create an IAM (Identity and Access Management) user with the necessary permissions to provision resources on AWS. Additionally, generate an IAM Access Key and Secret Access Key for programmatic access. Ensure that you securely manage these credentials.
4. S3 Bucket: Set up an S3 bucket to store your Terraform state files. This bucket is crucial for maintaining the state of your infrastructure and enabling collaboration.
5. Terraform: Install Terraform on your local machine. Terraform is used for provisioning infrastructure as code and managing AWS resources. Make sure to configure Terraform to work with your AWS credentials and your S3 bucket for state storage.

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


## STEP-1: Creating a EC2 instance with Following configurations using Terraform.

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
### *Note: You need to install the terraform on your local machine to run the above tf commands. ( Jenkins, docker, sonarqube container, trivy, terraform, kubectl and aws cli are also install on above created Jenkins_instance)


## STEP-2: Setting up Jenkins Pipeline
With Jenkins up and running, you configure pipelines to automate the end-to-end CI/CD process. The pipelines are responsible for orchestrating the entire workflow, from provisioning AWS EKS clusters with Terraform to deploying applications to EKS with ArgoCD. These pipelines ensure consistency and efficiency in your DevOps practices.

#### Borwse the <ip_of_newly_created_instance:8080>

1. ssh to the newly created instance.
2. cat /var/lib/jenkins/secrets/initialAdminPassword

##### Installing necessary puglins on the jenkins server : Go to Jenkins dashboard -> Manage Jenkins -> Manage Plugins -> Available tab.
1. terraform
2. 

##### Configuration of the Tools: Go to Dashboard > Manage Jenkins > System Configuration-tools
1. search for terraform.
2. give name: terraform
3. click on install automatically
4. apply and save.

#### First Job for terraform.
1. Click on new job on jenkins dashboard.
2. Give name: terraform-project-bsl
3. pipeline
4. ok
5. click on "discard old builds->Max of builds to keep:3"
6. Click on "This project is paramaterized-> Add Parameter->Choice Parameter->Give Name:Action and Choices: apply and destory"
7. Pipeline:
```
pipeline{
    agent any
    stages {
        stage('Checkout from Git'){
            steps{
                git branch: 'main', url: 'https://github.com/bishaldml/Tetris-V1.git'
            }
        }
        stage('Terraform version'){
             steps{
                 sh 'terraform --version'
             }
        }
        stage('Terraform init'){
             steps{
                 dir('Eks-terraform') {
                      sh 'terraform init'
                   }
             }
        }
        stage('Terraform validate'){
             steps{
                 dir('Eks-terraform') {
                      sh 'terraform validate'
                   }
             }
        }
        stage('Terraform plan'){
             steps{
                 dir('Eks-terraform') {
                      sh 'terraform plan'
                   }
             }
        }
        stage('Terraform apply/destroy'){
             steps{
                 dir('Eks-terraform') {
                      sh 'terraform ${action} --auto-approve'
                   }
             }
        }
    }
}
```
## STEP-


## STEP-



## STEP-




## STEP-
