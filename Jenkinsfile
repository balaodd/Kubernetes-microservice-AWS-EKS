pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test Environment') {
            steps {
                sh 'docker --version'
                sh 'aws --version'
                sh 'trivy --config /dev/null --version'
            }
        }
    }
}
