pipeline {
    agent any

    environment {
        DOCKER_USERNAME = 'venkateshaws'
        DOCKER_PASSWORD = 'Docker_AWS1258'
        DOCKER_IMAGE = "venkateshaws/my-app"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/venkey12319/Python-jenkins-PP-1.git', credentialsId: 'venkat-docker-hub-v'
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
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_USERNAME, DOCKER_PASSWORD) {
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

    post {
        always {
            cleanWs() // Clean up the workspace after running the pipeline
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
