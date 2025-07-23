pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/yourusername/yourrepo.git'
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
