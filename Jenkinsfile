pipeline{
    agent any
    environment {
        AWS_ACCOUNT_ID="548924361033"
        AWS_DEFAULT_REGION="us-east-1" 
        AWS_ACCESS_KEY_ID = credentials('aws_access_key_id')
        AWS_SECRET_ACCESS_KEY = credentials('aws_secret_access_key')
    }
    stages {
        stage('Checkout from Git'){
            steps{
                git branch: 'main', url: 'https://github.com/Bisi-23/Uber_clone.git'
            }
        }
        stage('Terraform version'){
             steps{
                 sh 'terraform --version'
             }
        }
        stage('Terraform init'){           
           steps{
                dir('EKS_Terraform') {
                      sh 'terraform init'
                   }
             }
        }
        stage('Terraform validate'){
             steps{
                 dir('EKS_Terraform') {
                      sh 'terraform validate'
                   }
             }
        }
        stage('Terraform plan'){
             steps{
                 dir('EKS_Terraform') {
                      sh 'terraform plan'
                   }
             }
        }
        stage('Terraform apply/destroy'){
             steps{
                 dir('EKS_Terraform') {
                      sh 'terraform ${action} --auto-approve'
                   }
             }
        }
    }
}  
