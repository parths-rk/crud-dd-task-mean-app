pipeline {
    agent any

    stages {

         stage('Build Backend Image') {
            steps {
                sh 'docker build -t mean-backend:${BUILD_TAG} ./backend'
                sh 'docker tag mean-backend:${BUILD_TAG} mean-backend:latest'
            }
        }


        stage('Build Frontend Image') {
            steps {
                sh 'docker build -t mean-frontend:${BUILD_TAG} ./frontend'
                sh 'docker tag mean-frontend:${BUILD_TAG} mean-frontend:latest'
            }
        }

        stage('Deploy Containers'){
            steps {
                sh 'docker compose down --remove-orphans || true' 
                sh 'docker compose up -d'
            }
        }
    }
}