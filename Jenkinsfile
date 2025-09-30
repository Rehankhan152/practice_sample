pipeline {
    agent any

    environment {
        COMPOSE_FILE = "docker-compose.yml"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Rehankhan152/practice_sample.git', branch: 'main'
            }
        }
        
        stage('Pull Images') {
            steps {
                echo 'Pulling Docker images...'
                sh 'docker pull rehan568388/practice-app:v1'
                sh 'docker pull rehan568388/zenput-frontend:v1'
            }
        }

        stage('Deploy Containers') {
            steps {
                echo 'Deploying QA environment...'
                sh "docker-compose -f $COMPOSE_FILE up -d"
            }
        }

        stage('Verify') {
            steps {
                echo 'Checking running containers...'
                sh 'docker ps'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished'
        }
    }
}
