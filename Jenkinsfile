pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/AbinSinghK/jenkins'
            }
        }
        stage('Deploy') {
            steps {
                input(id: 'deployApproval', message: 'Deploy to Production?', submitter: 'user1,user2')
                // Continue with deployment after approval
                echo "Deploying to production..."
                echo "abin"
            }
        }
        stage('Terraform init') {
            steps {
                sh 'terraform init'
               
            }
        }
        
        stage('Terraform Apply'){
            steps{
                sh ("terraform apply -auto-approve")
             }
        }
        stage('Terraform destroy'){
            steps{
                sh ("terraform destroy -auto-approve")
             }
        }
        stage('Post-Deployment') {
            steps {
                // Post-deployment steps here
                echo "Success"
            }
        }
    }
}
