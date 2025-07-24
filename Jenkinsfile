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
        sh 'docker run -d -p 8090:8000 fastapi-app:23'

    }
}

    }
}

