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

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push Images') {
            steps {
                sh 'docker push $DOCKER_USER/mean-backend:$BUILD_TAG'
                sh 'docker push $DOCKER_USER/mean-backend:latest'
                sh 'docker push $DOCKER_USER/mean-frontend:$BUILD_TAG'
                sh 'docker push $DOCKER_USER/mean-frontend:latest'
            }
        }

        stage('Deploy Containers') {
            steps {
                sh 'docker compose down --remove-orphans || true'
                sh 'docker compose up -d'
            }
        }
    }
}