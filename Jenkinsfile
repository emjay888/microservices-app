pipeline {
    agent any

    stages {
        stage('Build Frontend Image') {
            steps {
                script {
                    docker.build("frontend:latest", "./frontend")
                }
            }
        }

        stage('Build Backend Image') {
            steps {
                script {
                    docker.build("backend:latest", "./backend")
                }
            }
        }

       stage('Deploy') {
    steps {
        script {
            try {
                sh 'docker run -d -p 80:80 frontend:latest'
                sh 'docker run -d -p 3000:3000 backend:latest'
            } catch (Exception e) {
                echo "Caught: ${e}"
                currentBuild.result = 'FAILURE'
            }
        }
    }
}
