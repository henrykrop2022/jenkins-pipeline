pipeline {
    agent any
    stages {
        stage('clone') {
            steps {
                sh ' echo "cloning repo"'
            }
        }
        stage('Test') {
            steps {
                sh "echo 'Testing..'"
            }
        }
        stage('create file') {
            steps {
               sh ' touch text-${BUILD_ID}'
            }
        }
    }
}