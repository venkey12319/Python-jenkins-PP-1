pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('123456')
        DOCKER_IMAGE = "yourdockerhubusername/my-app"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/venkey12319/Python-jenkins-PP-1.git', credentialsId: '123456'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${DOCKER_IMAGE}:latest")
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials-id') {
                        dockerImage.push()
                    }
                }
            }
        }

        stage('Cleanup') {
            steps {
                sh 'docker rmi ${DOCKER_IMAGE}:latest'
            }
        }
    }
}