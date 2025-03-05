pipeline {
    agent any
    stages {
        stage('CodeScan') {
            steps {
                sh ' trivy fs .  -o result.html '        
                }
        }
        stage('dockerImageBuild') {
            steps {
                sh ' docker -v'
            }
        }
        stage('PushImage') {
            steps {
               sh ' docker ps'
            }
        }
    }
}