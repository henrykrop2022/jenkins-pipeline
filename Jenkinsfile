pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                sh 'cloning repo'
            }
        }
        stage('Test') {
            steps {
                sh 'Testing'
            }
        }
        stage('Create file') {
            steps {
               sh ' touch text-${BUILD_ID}'
            }
        }
    }
}