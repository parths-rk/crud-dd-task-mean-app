pipeline {
    agent any

    stages {
        stage('Clone Repository'){
            steps {
                git url://github.com/parths-rk/crud-dd-task-mean-app
            }
        }

        stage('Build Frontend Image') {
            steps {
                sh 'docker-build -t mean-frontend ./frontend'
            }
        }

        stage('Deploy Containers'){
            steps {
                sh 'docker compose down'
                sh 'docker compose up -d'
            }
        }
    }
}