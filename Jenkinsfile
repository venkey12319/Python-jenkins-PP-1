pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/venkey12319/Python-jenkins-PP-1.git', credentialsId: 'venkat-docker-hub-v'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("venkateshaws/my-app:latest")
                }
            }
        }

        stage('Cleanup') {
            steps {
                sh 'docker rmi venkateshaws/my-app:latest'
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
