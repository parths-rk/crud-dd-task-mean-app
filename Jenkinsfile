pipeline {
    agent any

    stages {


        stage('Build Frontend Image') {
            steps {
                sh 'docker build -t mean-frontend ./frontend'
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