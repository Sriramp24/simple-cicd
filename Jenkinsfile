pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Remove Old Container') {
            steps {
                sh '''
                docker stop nginx-container || true
                docker rm nginx-container || true
                '''
            }
        }

        stage('Run Nginx Container') {
            steps {
                sh '''
                docker pull nginx:latest

                docker run -d \
                --name nginx-container \
                -p 8080:80 \
                nginx:latest
                '''
            }
        }

        stage('Verify') {
            steps {
                sh 'docker ps'
            }
        }
    }
}
