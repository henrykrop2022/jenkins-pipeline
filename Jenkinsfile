pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                sh ' echo "cloning repo"'
            }
        }
        stage('Test') {
            steps {
                sh ' echo "Testing"'
            }
        }
        stage('Create file') {
            steps {
               sh ' echo "touch text-${BUILD_ID}"'
            }
        }
    }
}