pipeline {
    agent any
    stages {
        stage('CodeScan') {
            steps {
                sh ' trivy fs .  -o result.html '       
                }
        }
        stage('CodeLogin') {
            steps {
                sh ' aws ecr get-login-password --region us-east-1 | docker \
                login --username AWS --password-stdin 180294207776.dkr.ecr.us-east-1.amazonaws.com'
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
                sh ' docker tag jenkins-ci:latest \
                180294207776.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:latest'
                sh ' docker tag imageversion \
                180294207776.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:v1.$BUILD_NUMBER'
            }
        }
        stage('Docker PushImage to ECR') {
            steps {
               sh ' docker push 180294207776.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:latest'
                sh ' docker push 180294207776.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:v1.$BUILD_NUMBER'
            }
        }
    }
}