pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/ridha-gn/devops-fastapi-project'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('my-fastapi-app')
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    docker.image('my-fastapi-app').run('-p 8000:8000')
                }
            }
        }
    }
}
