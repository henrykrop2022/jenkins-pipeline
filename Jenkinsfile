pipeline {
    agent any

    environment {
        AWS_REGION = 'us-east-1'
        AWS_REPO = '180294207776.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci'
        AWS_URL = '180294207776.dkr.ecr.us-east-1.amazonaws.com'
    }
    stages {
        stage('CodeScan') {
            steps {
                sh ' trivy fs .  -o result.html '       
                }
        }
        stage('CodeLogin') {
            steps {
                sh " aws ecr get-login-password --region $AWS_REGION | docker login --username AWS --password-stdin $AWS_URL"
            }
        }
        stage('DockerImageBuild') {
            steps {
                sh ' docker build -t jenkins-ci .'
                sh ' docker build -t imageversion .'
            }
        }
        stage('DockerImageTag') {
            steps {
                sh " docker tag jenkins-ci:latest $ECR_REPO:latest"
                sh " docker tag imageversion $ECR_REPO:v1.$BUILD_NUMBER"
            }
        }
        stage('Docker PushImage to ECR') {
            steps {
               sh " docker push $ECR_REPO:latest"
                sh "docker push $ECR_REPO:v1.$BUILD_NUMBER" 
            }
        }
    }
}