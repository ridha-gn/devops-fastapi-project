pipeline {
    agent any

    environment {
        IMAGE_NAME = 'fastapi-app'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ridha-gn/devops-fastapi-project'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t ${IMAGE_NAME}:${BUILD_NUMBER} ."
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh "docker run -d -p 8000:8000 ${IMAGE_NAME}:${BUILD_NUMBER}"
                }
            }
        }
    }
}

