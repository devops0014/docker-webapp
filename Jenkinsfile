pipeline {
    agent any

    environment {
        DOCKER_COMPOSE_FILE = 'compose.yml'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'teja', url: 'https://github.com/RAVITEJA3929/docker-webapp.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                script {
                    sh 'docker-compose -f ${compose.yml} build'
                }
            }
        }

        stage('Deploy Application') {
            steps {
                script {
                    sh 'docker-compose -f ${compose.yml} up -d'
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
