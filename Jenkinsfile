pipeline {
    agent any

    environment {
        AWS_REGION = 'ap-south-1'
        AWS_ACCOUNT_ID = '774569412660'
        ECR_REGISTRY = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com"
        FRONTEND_IMAGE = "${ECR_REGISTRY}/frontend-app"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Frontend Docker Image') {
            steps {
                sh '''
                    docker build \
                    -t ${FRONTEND_IMAGE}:${BUILD_NUMBER} \
                    ./frontend
                '''
            }
        }

        stage('Trivy Image Scan') {
            steps {
                sh '''
                    trivy --config /dev/null image \
                    --severity HIGH,CRITICAL \
                    --exit-code 0 \
                    ${FRONTEND_IMAGE}:${BUILD_NUMBER}
                '''
            }
        }
    }
}
