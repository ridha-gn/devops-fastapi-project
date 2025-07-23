pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/ridha-gn/devops-fastapi-project.git'
        IMAGE_NAME = 'fastapi-app'
      
        BRANCH_NAME = 'main'
        GIT_CREDENTIALS_ID = 'b278af6a-9da4-4130-87bd-bc050208161b'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git credentialsId: "${GIT_CREDENTIALS_ID}", url: "${REPO_URL}", branch: "${BRANCH_NAME}"
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Run Docker Container (Local)') {
            steps {
                script {
                    sh "docker run -d -p 8000:8000 --name fastapi-container ${IMAGE_NAME}"
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // Only if using Kubernetes
                    sh '''
                    kubectl delete deployment fastapi-deployment --ignore-not-found=true
                    kubectl apply -f k8s/deployment.yaml
                    kubectl apply -f k8s/service.yaml
                    '''
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            sh "docker rm -f fastapi-container || true"
        }
        success {
            echo '✅ Pipeline finished successfully!'
        }
        failure {
            echo '❌ Pipeline failed.'
        }
    }
}
