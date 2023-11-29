pipeline {
    agent any

    stages {
        stage('Build Frontend Image') {
            steps {
                dir('microservices-app') {
                    sh 'docker build -t "frontend:latest" ./frontend'
                }
            }
        }

        stage('Build Backend Image') {
            steps {
                dir('microservices-app') {
                    sh 'docker build -t "backend:latest" ./backend'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Assuming you have a Docker daemon running on Jenkins
                    sh 'docker run -d -p 80:80 frontend:latest'
                    sh 'docker run -d -p 3000:3000 backend:latest'
                }
            }
        }
    }
}
