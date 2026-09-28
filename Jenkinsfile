pipeline {
    agent any

    environment {
        APP_NAME = 'jenkins-pipeline-app'
        CONTAINER_NAME = 'jenkins-pipeline-container'
        APP_PORT = '8081'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Code has been checked out from GitHub'
            }
        }

        stage('Test') {
            steps {
                echo 'Running application tests...'
                sh 'test -f index.html'
                echo 'Test passed!'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $APP_NAME:latest .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker rm -f $CONTAINER_NAME || true'
                sh 'docker run -d --name $CONTAINER_NAME -p $APP_PORT:80 $APP_NAME:latest'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
