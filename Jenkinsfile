pipeline {
    agent any

    parameters {
        choice(
            name: 'DEPLOY_APP',
            choices: ['Yes', 'No'],
            description: 'Do you want to deploy the application?'
        )
    }

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

        stage('Credentials Test') {
            steps {
                withCredentials([
                    string(
                        credentialsId: 'demo-secret',
                        variable: 'MY_SECRET'
                    )
                ]) {
                    sh 'echo "Credential successfully loaded into Jenkins"'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $APP_NAME:latest .'
            }
        }

        stage('Run Docker Container') {
            when {
                expression {
                    params.DEPLOY_APP == 'Yes'
                }
            }

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
