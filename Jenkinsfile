pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code successfully checked out from GitHub'
            }
        }

        stage('Environment Check') {
            steps {
                sh 'git --version'
                sh 'docker --version'
                sh 'aws --version'
                sh 'kubectl version --client'
            }
        }

        stage('Build Test') {
            steps {
                echo 'Jenkins pipeline is working successfully!'
            }
        }
    }

    post {
        success {
            echo 'CI pipeline completed successfully.'
        }

        failure {
            echo 'CI pipeline failed.'
        }
    }
}
