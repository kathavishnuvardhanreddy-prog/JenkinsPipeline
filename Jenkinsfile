pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting code from GitHub...'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-pipeline-app:latest .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker rm -f jenkins-pipeline-container || true'
                sh 'docker run -d --name jenkins-pipeline-container -p 8081:80 jenkins-pipeline-app:latest'
            }
        }
    }
}
