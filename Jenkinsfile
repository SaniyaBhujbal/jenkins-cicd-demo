pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building Docker image...'
                bat 'docker build -t jenkins-cicd-demo .'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Docker image...'
                bat 'docker run --rm jenkins-cicd-demo nginx -t'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                bat 'docker rm -f jenkins-demo 2>nul || exit /b 0'
                bat 'docker run -d -p 8090:80 --name jenkins-demo jenkins-cicd-demo'
            }
        }

    }
}